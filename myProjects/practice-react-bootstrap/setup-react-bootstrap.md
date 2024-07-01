
## インストール
```sh
npm install react-bootstrap bootstrap
```

## コンポーネントのインポート

```tsx
import Button from 'react-bootstrap/Button';

// or less ideally
import { Button } from 'react-bootstrap';
```

## SCSS インポート

```tsx
/* make the customizations */
$theme-colors: (
  'info': tomato,
  'danger': teal
);

@import "node_modules/bootstrap/scss/bootstrap";
```

> [!CAUTION]
> `@import '~bootstrap/scss/bootstrap';` これだと読み取りができないことがあるらしいので、`@import '~bootstrap/scss/bootstrap';` とする
> [javascript - Error: File to import not found or unreadable: ~bootstrap/scss/bootstrap - Stack Overflow](https://stackoverflow.com/questions/48434762/error-file-to-import-not-found-or-unreadable-bootstrap-scss-bootstrap)


