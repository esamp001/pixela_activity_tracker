
# Pixela API Interaction Script

This script demonstrates how to interact with the [Pixela API](https://pixe.la/) for tracking habits, such as the number of steps taken each day. The script is written in Python and leverages the `requests` library for HTTP requests.

## Prerequisites

- **Python 3.x**: Ensure Python is installed on your system.

- **Required Libraries**: Install the following Python libraries:
  - `requests`
  - `pytz`

  Install them using pip:
  ```bash
  pip install requests pytz
  ```

- **Pixela Account**: Create a Pixela account to obtain your `username` and `token`. Refer to [Pixela's User Creation API](https://pixe.la/#/post-user) for detailed instructions.

## Script Overview

### Features

1. Create a user on Pixela (optional and commented out).
2. Create a graph for habit tracking (optional and commented out).
3. Log daily habit values (e.g., number of steps).
4. Update existing habit values.
5. Delete habit values.

### Configuration

Customize the following variables in the script for your Pixela account:

- `USERNAME`: Your Pixela username.
- `TOKEN`: Your unique authentication token.
- `GRAPH_ID`: An identifier for your graph.

### Endpoints

The script communicates with these endpoints:

- `https://pixe.la/v1/users`: For user creation.
- `https://pixe.la/v1/users/{USERNAME}/graphs`: For graph creation.
- `https://pixe.la/v1/users/{USERNAME}/graphs/{GRAPH_ID}`: For posting, updating, and deleting graph values.

## How to Use

### 1. Set Up the User
To create a new Pixela user, uncomment the following lines in the script:

```python
response = requests.post(url=pixela_endpoint, json=user_params)
print(response.text)
```

Run the script to execute the user creation request.

### 2. Create a Graph
To create a graph for tracking habits, uncomment the following lines:

```python
response = requests.post(url=graph_endpoint, json=graph_config, headers=headers)
print(response.text)
```

Run the script to create your graph.

### 3. Log Daily Habit Values
To post the number of steps taken today:

- Run the script and enter the number of steps when prompted.
- The `post_value` dictionary sends the data to the `POST` endpoint.

Uncomment the following lines for posting values:

```python
response = requests.post(url=post_value_endpoint, json=post_value, headers=headers)
print(response.text)
```

### 4. Update Habit Values
To update the value for the current date:

- Modify the `quantity` field in `post_value` as needed.
- The `PUT` method updates the data.

Uncomment the following lines for updating values:

```python
response = requests.put(url=put_value_endpoint, json=post_value, headers=headers)
print(response)
```

### 5. Delete Habit Values
To delete the habit value for the current date:

- Use the `DELETE` method with the `delete_value_endpoint`.

Uncomment the following lines for deletion:

```python
response = requests.delete(url=delete_value_endpoint, headers=headers)
print(response.text)
```

## Additional Notes

- The `pytz` library ensures the date is set in the `Asia/Manila` timezone.
- The `datetime` module generates the current date in the `YYYYMMDD` format for Pixela API compatibility.
- Store sensitive data (e.g., `TOKEN`) securely. Avoid hardcoding them in production environments.

## Example Output

When posting a daily value, you should see a response like this:

```json
{
  "message": "Success.",
  "isSuccess": true
}
```

## License

This script is open for personal use and adaptation. Please adhere to Pixela's API usage policies.

## Author

[esamp001](https://github.com/esamp001)
