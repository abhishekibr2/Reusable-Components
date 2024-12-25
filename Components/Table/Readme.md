# Reusable Table Component Guide

The **Reusable Table Component** simplifies table creation and customization in your application. By passing a configuration object, you can easily define table behaviors, styles, and features. This guide provides a comprehensive overview of how to use and configure the component.

---

## Features
- **Dynamic Columns:** Define columns with different types, visibility, and behavior.
- **Custom Styles:** Apply styles to various parts of the table.
- **Sorting & Filtering:** Enable powerful data manipulation tools.
- **Search:** Add a search bar with configurable searchable columns.
- **Pagination:** Manage large datasets with paginated views.
- **Export & Import:** Export data to CSV, Excel, or PDF and import from CSV.
- **Editable Rows:** Allow inline editing with validation.
- **Kanban View:** Convert table data into a Kanban board.
- **Select & Bulk Edit:** Enable row selection and bulk editing capabilities.

---

## Installation

Ensure you have the necessary dependencies installed in your project. Then, import the component and the configuration:

```tsx
"use client"
import { TableComponent } from "@/components/ReusableUI/Table/Table";
import { ReusableTableConfig } from "@/config/Table/User";
```

---

## Basic Usage

### Example Code:
```tsx
export default function Home() {
    return (
        <main>
            <TableComponent config={ReusableTableConfig} endpoint="Users" />
        </main>
    );
}
```

### Key Props
- **`config`**: The configuration object defining table behavior and appearance.
- **`endpoint`**: The API endpoint to fetch data for the table.
- **`populate`** (optional): Defines how to populate specific fields.

---

## Configuration Schema

The `TableConfig` object allows extensive customization. Below is a breakdown of its properties:

### **General Properties**
| Property          | Type           | Description                             |
|-------------------|----------------|-----------------------------------------|
| `id`              | `string`       | Unique identifier for the table.        |
| `title`           | `string`       | Title displayed above the table.        |
| `description`     | `string`       | Description displayed below the title.  |

### **Column Definitions**

Define table columns with the following:
| Property          | Type           | Description                             |
|-------------------|----------------|-----------------------------------------|
| `id`              | `string`       | Unique column identifier.               |
| `header`          | `string`       | Column header text.                     |
| `accessorKey`     | `string`       | Key to access data for the column.      |
| `type`            | `ColumnType`   | Column data type.                       |
| `sortable`        | `boolean`      | Enable sorting on the column.           |
| `filterable`      | `boolean`      | Enable filtering on the column.         |
| `editable`        | `boolean`      | Allow inline editing for this column.   |
| `editConfig`      | `FormFieldConfig` | Configuration for inline editing.    |
| `options`         | `Array<{label, value}>` | Dropdown options for `select` type columns. |

### **Styles**
Customize the table appearance with:
| Property          | Type           | Description                             |
|-------------------|----------------|-----------------------------------------|
| `table`           | `string`       | CSS class for the table element.        |
| `header`          | `string`       | CSS class for the header section.       |
| `body`            | `string`       | CSS class for the body section.         |
| `noResults`       | `string`       | CSS class for the "no results" text.   |

### **Pagination**
Control pagination behavior:
| Property          | Type           | Description                             |
|-------------------|----------------|-----------------------------------------|
| `enabled`         | `boolean`      | Enable pagination.                      |
| `pageSize`        | `number`       | Default number of rows per page.        |
| `pageSizeOptions` | `number[]`     | Available page size options.            |

### **Search**
Enable and configure search capabilities:
| Property          | Type           | Description                             |
|-------------------|----------------|-----------------------------------------|
| `enabled`         | `boolean`      | Enable search functionality.            |
| `placeholder`     | `string`       | Placeholder text for the search bar.    |
| `searchableColumns` | `string[]`   | Columns that are searchable.            |

### **Advanced Features**
#### Filters
Enable filtering with supported operators:
| Property          | Type           | Description                             |
|-------------------|----------------|-----------------------------------------|
| `enabled`         | `boolean`      | Enable filtering functionality.         |
| `operators`       | `FilterOperator[]` | Supported filter operators.         |

#### Export & Import
Enable exporting and importing table data:
| Property          | Type           | Description                             |
|-------------------|----------------|-----------------------------------------|
| `enabled`         | `boolean`      | Enable data export/import functionality. |
| `formats`         | `Array<'csv' | 'excel' | 'pdf'>` | Supported formats. |

#### Kanban View
Switch between table and Kanban views:
| Property          | Type           | Description                             |
|-------------------|----------------|-----------------------------------------|
| `enabled`         | `boolean`      | Enable Kanban view.                     |
| `identification`  | `string`       | Key to identify tasks.                  |
| `columnOptions`   | `string[]`     | Possible Kanban column values.          |

#### Row Selection
Enable row selection with optional bulk actions:
| Property          | Type           | Description                             |
|-------------------|----------------|-----------------------------------------|
| `enabled`         | `boolean`      | Enable row selection.                   |
| `type`            | `'single' | 'multiple'` | Selection type.                  |
| `onSelect`        | `(selectedRows: any[]) => void` | Callback for selection. |

---
