# Command examples for redis.io

## How to add examples

- Create a test file with a meaningful name in the current folder. The file must end in `Example.cs`. For example `SetGetExample.cs`.
- The file should have a single method named `run` where the functionality is shown.
- Find out what's the example id for the example you're creating and add it as the first line of the file `// EXAMPLE: set_and_get`. More info below.


### Special markup

#### EXAMPLE:
Every file should contain an example id so it can be matched to the doc page it should show up on. You can check out the markdown file for that command to find the id, or if it hasn't been yet added in there, reach out to the docs team to agree on one.


#### HIDE_START and HIDE_END
Should be used to hide imports, connection creation and other bootstrapping code that is not important
for understanding a command example.

Example:

```csharp
// EXAMPLE: set_and_get
// HIDE_START
using System;
using StackExchange.Redis;

namespace Doc;

public class SetGetExample
{
    //TODO: Let the parser remove the annotations
    [Fact]
    public void run()
    {
        var redis = ConnectionMultiplexer.Connect("localhost:6379");
        var db = redis.GetDatabase();

        //HIDE_END
        bool status = db.StringSet("bike:1", "Process 134");
            
        if (status)
            Console.WriteLine("Successfully added a bike.");

        var value = db.StringGet("bike:1");

        if (value.HasValue)
            Console.WriteLine("The name of the bike is: " + value + ".");

        //REMOVE_START
        Assert.True(status);
        Assert.Equal("Process 134", value.ToString());
        //REMOVE_END
    //HIDE_START
    }
}
//HIDE_END
```

#### REMOVE_START and REMOVE_END
Should be used to **remove** code from the resulting code snippet published on redis.io.
This markup can be useful to remove assertions, and any eventual other testing blocks.

## How to test the examples

- TODO
