# VSCode Setup

## Extensions

- Editor Zoom | EasyZoom

- markdownlint

- PHP IntelliSense

- Twig

- VSCode Great Icons

## Configuration

- To remove the status workbench feedback.
    ```text
    "workbench.statusBar.feedback.visible": false,
    ``` 

- To add ruler in the editor view.
    ```text
    "editor.rulers": [
        100
    ],
    ```

- To auto add new line in every save files.
    - [Visual Studio Code — Insert New Line at the End of Files - Stack Overflow](https://stackoverflow.com/questions/44704968/visual-studio-code-insert-new-line-at-the-end-of-files)
    - Add this to the File > Preferences > Settings
    ```text
    files.insertFinalNewline": true
    ```
