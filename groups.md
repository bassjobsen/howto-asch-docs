# Using groups

## Setup a group
At the moment i do not know the exact use of the parameters when registering a group. See also [](). The source code tells us how to set them:

```
    if (!Number.isInteger(min) || min <= 0) return 'Min should be positive integer'
    if (!Number.isInteger(max) || max <= 0) return 'Max should be positive integer'
    if (!Number.isInteger(m) || m <= 0) return 'M should be positive integer'
    if (!Number.isInteger(updateInterval) || updateInterval <= 0) return 'UpdateInterval should be positive integer'

    if (min < 3) return 'Min should be greater than 3'
    if (min >= max) return 'Max should be greater than min'
    if (updateInterval < 1) return 'UpdateInterval should be greater than 1'
```

### group members
Registering a group also requires a list of group members. Again the code tells us the requirements for these members:

```

```