```csharp
public class Base
{
    public virtual void DoIt()
    {
    }
}

public class Derived : Base
{
    public override void DoIt()
    {
    }
}

Base b = new Derived();
b.DoIt();                      // Calls Derived.DoIt
```

/diffbot_base_controller/cmd_vel_unstamped