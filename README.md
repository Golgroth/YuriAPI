# YuriAPI

Use this API to simplify Spigot plugin development.

# Command creation

```
public class CustomCommand {

@Cmd(command = "customcommand")
public void customCmdRun(CommandClass c){
    c.getSender().sendMessage("working");
}
}
```

```
public class Main extends JavaPlugin {

    @Override
    public void onEnable (){
       CommandManager cmdmg = new CommandManager (this);
       cmdmg.register(new CustomCommand());
    }

}
```

#Get config.yml values using annotations

```
public class Main extends JavaPlugin {

    @ConfigVar(varname = "custom-variable")
    private String cfgVar;

    @Override
    public void onLoad (){
       ConfigVarManager.register(this);
    }

    @Override
    public void onEnable (){
       Bukkit.getConsoleSender().sendMessage(cfgVar);
    }

}
```
