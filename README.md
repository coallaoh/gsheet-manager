# GSheetManager

GSheetManager is a Python package that provides a convenient interface for managing Google Sheets. It offers features like batch updates, local caching, and automatic worksheet refreshing to optimize interactions with Google Sheets.

## Installation

You can install GSheetManager using pip:

```
pip install gsheet-manager
```

## Requirements

- Python 3.6+
- gspread library

## Usage

Here's a basic example of how to use GSheetManager:

```python
from gsheet_manager import GSheetManager

# Initialize the manager
manager = GSheetManager('path/to/key_file.json', 'Your Google Sheet Name', 'Your Worksheet Name')

# Use the batch_sync_with_remote decorator for operations
@GSheetManager.batch_sync_with_remote
def update_sheet(manager):
    # Your operations here
    manager._set_buffer_cells(0, 0, "New Value")

# Run your function
update_sheet(manager)
```

## Features

- Batch updates to minimize API calls
- Local caching of sheet values
- Automatic worksheet refreshing
- Decorator for syncing operations with remote

## API Reference

### GSheetManager(key_file, doc_name, sheet_name)

Creates a new GSheetManager instance.

- `key_file`: Path to your Google Service Account key file
- `doc_name`: Name of your Google Sheet
- `sheet_name`: Name of the worksheet

### Methods

- `refresh_worksheet()`: Refreshes the worksheet if the timeout has passed
- `sync_from_remote()`: Syncs local values from the remote sheet
- `batch_update_remote()`: Sends batched updates to the remote sheet
- `_set_buffer_cells(python_row_idx, python_col_idx, value)`: Sets a value in the local buffer

### Decorators

- `@batch_sync_with_remote`: Decorator for methods that need to sync with the remote sheet

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
