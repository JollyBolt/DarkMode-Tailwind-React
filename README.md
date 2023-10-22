# DarkMode-Tailwind-React
A guide to how to add dark mode feature with TailwindCSS to your react project.

1. Go to <span style="color:blue">tailwind.config.js</span> and add the follwing code:
```css
module.exports = {
    darkMode: 'class',
    // ...
}
```
![Screenshot 2023-10-20 at 2 50 15 PM](https://github.com/JollyBolt/DarkMode-Tailwind-React/assets/68071708/1f4fc426-7941-4f1e-ba12-a716ac8412cd)

2. Add the following script in your index.html file.
```js
<script>
    // On page load or when changing themes, best to add inline in `head` to avoid FOUC
    if (localStorage.getItem('color-theme') === 'dark' || (!('color-theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
        document.documentElement.classList.add('dark');
    } else {
        document.documentElement.classList.remove('dark')
    }
</script>
```
![Screenshot 2023-10-23 at 12 50 58 AM](https://github.com/JollyBolt/DarkMode-Tailwind-React/assets/68071708/ffcf6dac-b0c5-441e-82cb-5af052d0aa6f)

3. Create a button that will switch the theme.
```js
    <button 
    onClick={handleDarkMode}>
    {
        theme==='light'
        ?<LightModeOutlinedIcon />
        :<DarkModeOutlinedIcon />
    }
    </button>
```
4. Create the handleDarkMode function.
```js
const handleDarkMode = () =>{
        if (localStorage.getItem('color-theme')) {
            if (localStorage.getItem('color-theme') === 'light') {
                document.documentElement.classList.add('dark');
                localStorage.setItem('color-theme', 'dark');
                setTheme('dark')
            } else {
                document.documentElement.classList.remove('dark');
                localStorage.setItem('color-theme', 'light');
                setTheme('light')
            }
            
        } else {
            if (document.documentElement.classList.contains('dark')) {
                document.documentElement.classList.remove('dark');
                localStorage.setItem('color-theme', 'light');
                setTheme('light')               
            } else {
                document.documentElement.classList.add('dark');
                localStorage.setItem('color-theme', 'dark');
                setTheme('dark')
            }
        }
    }
```


