# Data Structure Documentation

## Overview
The theme park optimization data is stored in CSV files using a numeric ID-based system for easy maintenance and updating.

## File Descriptions

### 1. `data/attractions.csv`
Contains core information about each attraction.

**Columns:**
- `id` (int): Unique identifier for the attraction (1, 2, 3, ...)
- `name` (string): Display name of the attraction
- `preference` (int): Preference score (1-10, higher = more desirable)
- `ride_duration` (float): Duration of the ride in minutes

**Example:**
```csv
id,name,preference,ride_duration
1,Leviathan,10,3.5
2,Behemoth,9,3.0
```

### 2. `data/distances.csv`
Walking times between all locations (entrance and attractions) in n×n matrix format.

**Format:** Square matrix with (n_attractions + 1) × (n_attractions + 1) dimensions
- First row: Column headers with IDs (0, 1, 2, 3, 4, 5, ...)
- First column: Row headers with IDs (0, 1, 2, 3, 4, 5, ...)
- Matrix values: Walking time in minutes between locations
- ID 0 is reserved for the park Entrance
- Matrix must be **symmetric** (distance i→j = distance j→i)

**Example:**
```csv
,0,1,2,3,4,5
0,0,8,10,12,15,18
1,8,0,5,7,10,12
2,10,5,0,6,8,10
...
```

**Validation:** The notebook automatically validates:
- Matrix is square (rows = columns)
- Matrix is symmetric
- Size matches number of attractions + 1

### 3. `data/wait_times.csv`
Hourly wait times for each attraction throughout the day.

**Columns:**
- `id` (int): Attraction ID (matches `attractions.csv`)
- `9`, `10`, `11`, ..., `21`: Wait times (in minutes) for each hour of operation

**Example:**
```csv
id,9,10,11,12,13,14,15,16,17,18,19,20,21
1,15,25,35,45,50,55,60,50,40,30,20,15,10
```

## Benefits of ID-Based Structure

1. **Easy Name Changes**: Attraction names can be updated in `attractions.csv` only
2. **Referential Integrity**: IDs ensure consistency across all data files
3. **Efficiency**: Numeric IDs are faster to process than string comparisons
4. **Scalability**: Easy to add/remove attractions by managing IDs

## How to Update Data

### Adding a New Attraction
1. Add a row to `attractions.csv` with a new ID (e.g., 6)
2. Expand the `distances.csv` matrix to 7×7 (adding row and column for new ID)
3. Add a wait times row in `wait_times.csv` with the new ID

### Changing an Attraction Name
1. Simply update the `name` field in `attractions.csv`
2. No changes needed in other files!

### Updating Wait Times or Distances
1. Edit the corresponding CSV file directly
2. The notebook will automatically load the new data
