# 📊 Extended MUI-X DataGrid (Community Edition)

  

This project extends the **[MUI DataTable (Free Version)](https://mui.com/x/react-data-grid/)** by adding missing but important features for real-world applications such as **advanced filtering, server-side sorting, and pagination integration**.

  

---

![App Screenshot](docs/datatable3.png)

---

  

## ✨ Features

  

- 🔍 **Advanced Filtering**  

  - Complex filters with multiple fields, operators (`=`, `>`, `<`, `contains`, etc.), and logic operators (`and`, `or`).  

- 📑 **Server-Side Pagination**  

  - Support for `limit` and `offset` in API calls.  

- ↕ **Multi-Column Sorting**  

  - Pass sort instructions to the backend in a structured format.  

- 🌐 **REST-Friendly Query Encoding**  

  - Automatically encodes filter/sort objects into URL query parameters for GET requests.  

- ⚡ **Plug-and-Play Utility**  

  - Works with Axios or any fetch utility for smooth integration with APIs.  

- 🛠️ **TypeScript Support**  

  - Strongly typed utilities for safer integration in React + TS projects.

  

---

  

## ❓ Why This Repo?

  

The original **Mui-x Data Grid Free Edition** has some limitations:

- ❌ Lacks support for **complex filtering logic** (multiple columns with `and/or` linkOperator).  

- ❌ Lacks support for **complex sorting logic** (multiple column sort with `and/or` linkOperator`).  

  
  

This repo **fills the gaps** by:

- ✅ Adding advanced filter + sort utilities for server-side APIs.  

- ✅ Providing a clean way to encode/decode queries.  

- ✅ Ensuring compatibility with REST and GraphQL backends.  

- ✅ Writing everything with **TypeScript-first** design.  

  

---

  

## 📦 Installation

  

```bash

npm install dialeth-datagrid-mui-x

  

# install dependencies

npm install @mui/material @emotion/react @emotion/styled

npm install @mui/x-data-grid

  

```

  

---

  

## 🚀 Usage

  

### 1. In your React project

  

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

    

---

### 2. Props 

### 2. Request Payload Format

  

#### 🔹 POST (with payload)

  

```json

{

  "filter": {

    "items": [

      { "field": "name", "operator": "contains", "value": "Jane" },

      { "field": "age", "operator": ">", "value": "30" }

    ],

    "logicOperator": "and"

  },

  "sort": [

    { "field": "rating", "sort": "desc" },

    { "field": "name", "sort": "asc" }

  ],

  "limit": 30,

  "offset": 3

}

```

  

#### 🔹 GET (query params)

  

```

GET /api/players?

  filter=%7B%22items%22%3A%5B%7B%22field%22%3A%22name%22%2C%22operator%22%3A%22contains%22%2C%22value%22%3A%22Jane%22%7D%2C%7B%22field%22%3A%22age%22%2C%22operator%22%3A%22%3E%22%2C%22value%22%3A%2230%22%7D%5D%2C%22logicOperator%22%3A%22and%22%7D

  &sort=%5B%7B%22field%22%3A%22rating%22%2C%22sort%22%3A%22desc%22%7D%2C%7B%22field%22%3A%22name%22%2C%22sort%22%3A%22asc%22%7D%5D

  &limit=30

  &offset=3

```

  

---

  
  

## 🤝 Contributing

  

Contributions are welcome! Please open an issue first to discuss your idea.  

- Fork the repo  

- Create your feature branch (`git checkout -b feature/amazing-feature`)  

- Commit changes (`git commit -m 'Add amazing feature'`)  

- Push branch (`git push origin feature/amazing-feature`)  

- Open a pull request  

  

---

  

## 📜 License

  

MIT © [Your Name](https://github.com/aymarc)