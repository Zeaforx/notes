# XtendedMuiGrid

  

A powerful, feature-rich wrapper for Material-UI's DataGrid component that provides server-side filtering, sorting, pagination, and export capabilities out of the box.

  

## Features

  

- 🔍 **Advanced Filtering** - Multi-filter support with AND/OR logic operators

- 📊 **Server-Side Operations** - Built-in support for server-side filtering, sorting, and pagination

- 📥 **Export Functionality** - Export data to CSV or Excel formats

- 🎛️ **Custom Toolbar** - Pre-built toolbar with filter controls and export buttons

- 📄 **Flexible Pagination** - Standard pagination with "Jump to Page" functionality

- 🎯 **Row Context Menu** - Customizable row menu on click

- 🔧 **Configurable Filters** - Support for dropdown filters via filterMap

- 🚀 **GET/POST Support** - Flexible API request methods

- 📦 **TypeScript Support** - Full TypeScript definitions included

  

## Installation

  

```bash

npm install xtended-mui-grid @mui/x-data-grid @mui/material @emotion/react @emotion/styled

```

  

or with yarn:

  

```bash

yarn add xtended-mui-grid @mui/x-data-grid @mui/material @emotion/react @emotion/styled

```

  

## Peer Dependencies

  

This package requires the following peer dependencies:

  

- `@mui/x-data-grid`: ^6.0.0 or higher

- `@mui/material`: ^5.0.0 or higher

- `react`: ^18.0.0 or higher

- `react-dom`: ^18.0.0 or higher

  

## Basic Usage

  

```tsx

import React, { useState } from 'react';

import { XtendedMuiGrid } from 'xtended-mui-grid';

import { GridColDef } from '@mui/x-data-grid';

  

function MyDataGrid() {

  const [gridData, setGridData] = useState({ data: [], total: 0 });

  const [loading, setLoading] = useState(false);

  

  const columns: GridColDef[] = [

    { field: 'id', headerName: 'ID', width: 90 },

    { field: 'name', headerName: 'Name', width: 150 },

    { field: 'email', headerName: 'Email', width: 200 },

    { field: 'createdAt', headerName: 'Created At', width: 150 },

  ];

  

  const handleFilterChange = async (payload) => {

    setLoading(true);

    try {

      // Your API call here

      const response = await fetch(`/api/data?${payload.toString()}`);

      const result = await response.json();

      setGridData({ data: result.data, total: result.total });

    } catch (error) {

      console.error('Error fetching data:', error);

    } finally {

      setLoading(false);

    }

  };

  

  return (

    <XtendedMuiGrid

      columns={columns}

      gridData={gridData}

      handleFilterChange={handleFilterChange}

      defaultFilter={[]}

      externalLoading={loading}

      getRowId={(row) => row.id}

    />

  );

}

```

  

### 2. Props

#### Required Props

|   |   |   |
|---|---|---|
|**Prop**|**Type**|**Description**|
|`columns`|`GridColDef[]`|Array of column definitions following MUI DataGrid column structure|
|`gridData`|`{ data: any[], total: number }`|The data object containing rows and total count|
|`handleFilterChange`|`(payload: FilterPayloadDef) => void`|Callback function triggered when filters, sorting, or pagination changes|
|`defaultFilter`|`FilterItem[]`|Initial filter configuration to apply on component mount|

#### Optional Props

|                   |                                                                   |             |                                                            |
| ----------------- | ----------------------------------------------------------------- | ----------- | ---------------------------------------------------------- |
| **Prop**          | **Type**                                                          | **Default** | **Description**                                            |
| `externalLoading` | `boolean`                                                         | `false`     | Shows a loading indicator in the toolbar                   |
| `filterMap`       | `Record<string, any[]>`                                           | `undefined` | Map of field names to dropdown values for specific filters |
| `getRowId`        | `(row: any) => string`                                            | `undefined` | Function to extract unique row ID                          |
| `renderRowMenu`   | `(row: any, onClose: () => void) => JSX.Element`                  | `undefined` | Function to render custom row context menu                 |
| `handleExport`    | `(payload: FilterPayloadDef, fileType: 'csv' \| 'excel') => void` | `undefined` | Custom export handler function                             |
| `csvExportUrl`    | `string`                                                          | `undefined` | API endpoint for CSV export                                |
| `excelExportUrl`  | `string`                                                          | `undefined` | API endpoint for Excel export                              |
| `exportFileName`  | `string`                                                          | `'my-data'` | Base name for exported files                               |
| `fetchMode`       | `'get' \| 'post'`                                                 | `'get'`     | HTTP method for API requests                               |

### Filter Payload Structure

  

The `handleFilterChange` callback receives a payload with the following structure:

  

#### For GET requests (fetchMode: 'get'):

```typescript

URLSearchParams with:

- filter: JSON string of { items: FilterItem[], logicOperator?: 'and' | 'or' }

- sort: JSON string of { field: string, sort: 'asc' | 'desc' }[]

- limit: number (page size)

- offset: number (pagination offset)

```

  

#### For POST requests (fetchMode: 'post'):

```typescript

{

  filter: {

    items: FilterItem[],

    logicOperator?: 'and' | 'or'

  },

  sort: { field: string, sort: 'asc' | 'desc' }[],

  limit: number,

  offset: number

}

```

  

### FilterItem Structure

  

```typescript

{

  field: string;      // Column field name

  operator: string;   // 'equals', 'contains', '>', '<'

  value: string | number;

}

```

  

## Advanced Usage

  

### Using Dropdown Filters

  

For specific columns, you can provide predefined values via the `filterMap` prop:

  

```tsx

const filterMap = {

  status: ['Active', 'Inactive', 'Pending'],

  role: ['Admin', 'User', 'Guest'],

};

  

<XtendedMuiGrid

  columns={columns}

  gridData={gridData}

  handleFilterChange={handleFilterChange}

  defaultFilter={[]}

  filterMap={filterMap}

/>

```

  

### Custom Row Context Menu

  

```tsx

const renderRowMenu = (rowData, onClose) => (

  <>

    <MenuItem onClick={() => {

      console.log('Edit:', rowData);

      onClose();

    }}>

      Edit

    </MenuItem>

    <MenuItem onClick={() => {

      console.log('Delete:', rowData);

      onClose();

    }}>

      Delete

    </MenuItem>

  </>

);

  

<XtendedMuiGrid

  columns={columns}

  gridData={gridData}

  handleFilterChange={handleFilterChange}

  defaultFilter={[]}

  renderRowMenu={renderRowMenu}

/>

```

  

### Export with API Endpoints

  

```tsx

<XtendedMuiGrid

  columns={columns}

  gridData={gridData}

  handleFilterChange={handleFilterChange}

  defaultFilter={[]}

  csvExportUrl="/api/export/csv"

  excelExportUrl="/api/export/excel"

  exportFileName="users-export"

/>

```

  

The export URLs will receive the same filter/sort/pagination parameters as your data endpoint.

  

### Custom Export Handler

  

```tsx

const handleCustomExport = async (payload, fileType) => {

  const response = await fetch('/api/custom-export', {

    method: 'POST',

    headers: { 'Content-Type': 'application/json' },

    body: JSON.stringify({ ...payload, format: fileType }),

  });

  const blob = await response.blob();

  const url = URL.createObjectURL(blob);

  const link = document.createElement('a');

  link.href = url;

  link.download = `export-${Date.now()}.${fileType === 'csv' ? 'csv' : 'xlsx'}`;

  link.click();

};

  

<XtendedMuiGrid

  columns={columns}

  gridData={gridData}

  handleFilterChange={handleFilterChange}

  defaultFilter={[]}

  handleExport={handleCustomExport}

/>

```

  

### Using POST Method for API Requests

  

```tsx

const handleFilterChange = async (payload) => {

  const response = await fetch('/api/data', {

    method: 'POST',

    headers: { 'Content-Type': 'application/json' },

    body: JSON.stringify(payload),

  });

  const result = await response.json();

  setGridData({ data: result.data, total: result.total });

};

  

<XtendedMuiGrid

  columns={columns}

  gridData={gridData}

  handleFilterChange={handleFilterChange}

  defaultFilter={[]}

  fetchMode="post"

/>

```

  

### Default Filters

  

```tsx

const defaultFilter = [

  { field: 'status', operator: 'equals', value: 'Active' },

  { field: 'createdAt', operator: '>', value: '2024-01-01' },

];

  

<XtendedMuiGrid

  columns={columns}

  gridData={gridData}

  handleFilterChange={handleFilterChange}

  defaultFilter={defaultFilter}

/>

```

  

## Server-Side Implementation Examples

  

### Express.js Backend Example

  

```javascript

app.get('/api/data', async (req, res) => {

  const { filter, sort, limit, offset } = req.query;

  const filterObj = filter ? JSON.parse(filter) : { items: [] };

  const sortObj = sort ? JSON.parse(sort) : [];

  // Build your database query

  const query = buildQuery(filterObj, sortObj, limit, offset);

  const data = await db.query(query);

  const total = await db.count(buildCountQuery(filterObj));

  res.json({ data, total });

});

```

  

### Handling Filter Operators

  

```javascript

function buildWhereClause(filterItem) {

  const { field, operator, value } = filterItem;

  switch (operator) {

    case 'equals':

      return `${field} = '${value}'`;

    case 'contains':

      return `${field} LIKE '%${value}%'`;

    case '>':

      return `${field} > '${value}'`;

    case '<':

      return `${field} < '${value}'`;

    default:

      return '';

  }

}

  

function buildQuery(filterObj, sortObj, limit, offset) {

  let query = 'SELECT * FROM users';

  if (filterObj.items.length > 0) {

    const whereClauses = filterObj.items.map(buildWhereClause);

    const operator = filterObj.logicOperator === 'or' ? 'OR' : 'AND';

    query += ` WHERE ${whereClauses.join(` ${operator} `)}`;

  }

  if (sortObj.length > 0) {

    const orderBy = sortObj.map(s => `${s.field} ${s.sort.toUpperCase()}`).join(', ');

    query += ` ORDER BY ${orderBy}`;

  }

  query += ` LIMIT ${limit} OFFSET ${offset}`;

  return query;

}

```

  

## Component Architecture

  

The package consists of four main components:

  

1. **XtendedMuiGrid** - Main wrapper component that manages state and data fetching

2. **XtendedMuiGridToolbar** - Custom toolbar with filter controls and export buttons

3. **XtendedMuiGridPaginationControls** - Enhanced pagination with "Jump to Page" feature

4. **XtendedMuiGridRowMenu** - Optional row context menu

  

## Styling

  

The component uses Material-UI's theming system. You can customize the appearance by wrapping your app with a MUI ThemeProvider:

  

```tsx

import { createTheme, ThemeProvider } from '@mui/material/styles';

  

const theme = createTheme({

  palette: {

    primary: {

      main: '#1976d2',

    },

  },

});

  

function App() {

  return (

    <ThemeProvider theme={theme}>

      <XtendedMuiGrid {...props} />

    </ThemeProvider>

  );

}

```

  

## Best Practices

  

1. **Always provide a unique `getRowId`** - This ensures proper row identification and prevents rendering issues

2. **Handle loading states** - Use the `externalLoading` prop to show feedback during API calls

3. **Implement proper error handling** - Wrap your `handleFilterChange` in try-catch blocks

4. **Optimize server queries** - Use database indexes on filtered and sorted columns

5. **Validate filter inputs** - Sanitize user input on the server side to prevent injection attacks

6. **Consider pagination limits** - Set reasonable maximum page sizes to prevent performance issues

7. **Cache when possible** - Implement caching strategies for frequently accessed data

  

## Troubleshooting

  

### Data not loading

- Ensure `handleFilterChange` is properly updating `gridData`

- Check that your API endpoint returns data in the format `{ data: [], total: number }`

- Verify network requests in browser DevTools

  

### Filters not working

- Check that filter values match your data types

- Ensure server-side implementation correctly parses filter operators

- Verify `filterMap` values match actual data values

  

### Export not working

- Ensure either `handleExport` or export URLs are provided (not both)

- Check that export endpoints return proper file blobs

- Verify CORS settings if export endpoints are on different domains

  

## TypeScript Support

  

All types are exported from the package:

  

```typescript

import {

  CustomDataGridDef,

  FilterPayload,

  FilterPayloadDef,

  FilterItem,

  FETCH_MODE,

  GridColDef

} from 'xtended-mui-grid';

```

  

## License

  

MIT

  

## Contributing

  

Contributions are welcome! Please feel free to submit a Pull Request.

  

## Support

  

For issues and feature requests, please use the GitHub issue tracker.