# Angular Snippets

## How to hide mat-header-row (Column Name) ?
```html
    <mat-header-row 
        *cdkHeaderRowDef="['col1', 'col2']"
        style="display: none;">
    </mat-header-row>
```

