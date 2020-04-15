# YuriAPI

Use this API to simplify Spigot plugin development.

# Command creation

```java
public class CustomCommand {

@Cmd(command = "customcommand")
public void customCmdRun(CommandEvent c){
    c.getSender().sendMessage("working");
}
}
```

```java
public class Main extends JavaPlugin {

    @Override
    public void onEnable (){
       CommandManager cmdmg = new CommandManager (this);
       cmdmg.register(new CustomCommand());
    }

}
```

# Get config.yml values using annotations

```java
public class Main extends JavaPlugin {

    @ConfigVar(varname = "custom-variable")
    private String cfgVar;

    @ConfigVarExceptionListener
    public void onCfgException(ConfigVarException e){
        e.printStackTrace();
        Bukkit.shutdown();
    }

    @Override
    public void onLoad (){
       ConfigVarManager.register(this, this);
    }

    @Override
    public void onEnable (){
       ConfigVarManager.update(this);
       Bukkit.getConsoleSender().sendMessage(cfgVar);
    }

}
```
