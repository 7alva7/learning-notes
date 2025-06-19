# Note

## Sticky Header

```css
.sticky {
  position: sticky;
  top: 0;
}
```

## Smooth scrolling when switching between hash links

```css
html {
  scroll-behavior: smooth;
}
```

```jsx
import Link from 'next/link';

const Navigation = () => {
  return (
    <nav>
      <ul>
        <li>
          <Link href="#section1">Section 1</Link>
        </li>
        <li>
          <Link href="#section2">Section 2</Link>
        </li>
        <li>
          <Link href="#section3">Section 3</Link>
        </li>
      </ul>
    </nav>
  );
};

export default Navigation;
```