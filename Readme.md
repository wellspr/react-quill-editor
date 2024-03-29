# React Quill Editor

This is a react typescript wrapper for [Quill JS](https://quilljs.com). 

## Get started

All editor components and hooks must be children of a `Provider` component, which optionally accepts a `config` object containing custom options and custom fonts to be used in the project.

### Provider

```jsx
<Provider config={{ options: customOpt, fonts: customFonts }}>
    {children}
</Provider>
```

### Editor

The Editor component renders the editor on the screen, and expects a prop `height`. Bellow we render the Editor with a height of 300px. 

```jsx
<Editor height={300} />
```

One can also provide height as a string, including specific units, for example `height={"300px"}` or `height={"85%"}`.

### Custom Toolbar

A custom toolbar can be provided as a child of `Editor`.


## Example

`App.tsx`
```jsx
import { FC } from "react";
import MyEditorProvider from "./components/MyEditorProvider";
import MyEditor from "./components/MyEditor";

const App: FC = () => {
    return (
        <MyEditorProvider>
            <MyEditor />
        </MyEditorProvider>
    );
};

export default App;

```

`MyEditorProvider.tsx`
```jsx
import { FC, ReactNode } from "react";
import { Provider } from "react-quill-editor";
import { customOpt, customFonts } from "../config/myCustomConfig";

interface MyEditorProps {
    children: ReactNode;
}

const MyEditorProvider: FC<MyEditorProps> = ({ children }) => {
    return (
        <Provider config={{ options: customOpt, fonts: customFonts }}>
            {children}
        </Provider>
    );
};

export default MyEditorProvider;
```

`MyEditor.tsx`
```jsx
import { FC } from "react";
import Editor from "react-quill-editor";

const MyEditor: FC = () => {

    const { content } = useEditor();

    useEffect(() => {
        console.log(content);
    }, [content]);

    return (
        <Editor height={300} />
    );
};

export default MyEditor;
```

