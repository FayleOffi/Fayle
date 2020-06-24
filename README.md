<a href="https://fayle.fr"><img src="https://avatars2.githubusercontent.com/u/65917484?s=400&u=341ea26f0e1396e19eff286f80e7461bd408c5c5&v=4&s=200" title="Fayle" alt="Fayle"></a>

# Fayle(API Spigot)

> Simple Main Class

> Create connexion with Jedis for Redis quickly(unstable)

> Register your listeners / commands quickly

> Log system

> Inventory system simple with FastInv(Modified)

> Create item simply

> Cooldown system

> Command framework

> Use google gson simply

> Create your config file quickly

> Convert long to datetime

> Send actionbar / broadcast message simply

> Get if player has an full inventory

> Give a stuff

> Json persist

## Developpers

- Fayle

## Status

[![Build Status](http://img.shields.io/travis/badges/badgerbadgerbadger.svg?style=flat-square)](https://travis-ci.org/badges/badgerbadgerbadger)

---

## How to use ?

> Simple Main Class

```java 

public class Main extends Fay {


    @Override
    public void load() {
        init(this) // <-- Don't forget that
        //DO SOMETHING
    }

    @Override
    public void unLoad() {
        //DO SOMETHING
    }



}

```

> Register your listeners / commands quickly

```java 

addCommands(FayCommands faycommands)
addListeners(Listener listener)

```

> Registers JsonPersist

```java

registerPersist(JsonPersist persist);  //<== With JsonPersist

```

> Log system

```java

FayLog.log(Level level,String message);

```

> Inventory system simple with FastInv of MrMicky(Modified)

```java

public class ExampleInventory extends FayInv {

    private boolean preventClose = false;

    public ExampleInventory() {
        super(45, ChatColor.GOLD + "Example inventory");

        // Just add a random item
        setItem(22, new FayBuilder(Material.IRON_SWORD), e -> e.getWhoClicked().sendMessage("You clicked on the sword"));

        // Add some blocks to the borders
        setItems(getBorders(), new FayBuilder(Material.LAPIS_BLOCK).setName("§cI love you"));

        // Add a simple item to prevent closing the inventory
        setItem(34, new FayBuilder(Material.BARRIER).setName(ChatColor.RED + "Prevent close"), e -> {
            preventClose = !preventClose;
        });

        // Prevent from closing when preventClose is to true
        setCloseFilter(p -> preventClose);
    }

    @Override
    public void onOpen(InventoryOpenEvent event) {
        event.getPlayer().sendMessage(ChatColor.GOLD + "You opened the inventory");
    }

    @Override
    public void onClose(InventoryCloseEvent event) {
        event.getPlayer().sendMessage(ChatColor.GOLD + "You closed the inventory");
    }

    @Override
    public void onClick(InventoryClickEvent event) {
        // do something
    }
}

```

```java

new ExampleInventory().open(player); // To open the inventory

```

> Create item simply

```java

new FayBuilder(Material.LAPIS_BLOCK).setName("§dI'am magick !").setLore("I love","Magie","But I can't do it");

/*
* Add .build() at the end for transform FayBuilder to ItemStack
*/

```

> Cooldown system


```java

System.out.println("In work !");

```

> Command framework


```java

public class Commands extends FayCommands{
    @Override
    public String getName() {
        return "mycommands";
    }

    @Override
    public String getDescription() {
        return "This is a command for test !";
    }

    @Override
    public String getSyntaxe() {
        return "§c/mycommands";
    }

    @Override
    public String getAliases() {
        return "";
    }

    @Override
    public void perform(Player player, String[] args) {

    }
}


```

> Use google gson simply


```java

System.out.println("In work !");

```

> Create your config file quickly


```java

    private FileConfiguration myConfig;

    @Override
    public void load() {
       getConfigFile().createConfigFile("myconfig");
       myConfig = YamlConfiguration.loadConfiguration(getConfigFile().getFile("myconfig"));
    }


```

> Convert long to datetime


```java

FayTimer.getFormatLongDays(long temps);
FayTimer.getFormatLongHours(long temps);
FayTimer.getFormatLongHoursSimple(long temps);
FayTimer.getFormatLongMinutes(long temps);
FayTimer.getFormatLongSecondes(long temps);
FayTimer.getStringTime(long second);

```

> Send actionbar / broadcast message simply


```java

FayUtils.sendActionBar(Player player,String message);
FayUtils.sendActionBar(Player player, String message, int sec);
FayUtils.broadcastActionMessage(String paramString);
FayUtils.broadcastActionMessage(String paramString, int timer);

```

> Get if player has an full inventory


```java

FayUtils.hasInventoryFull(Player player);

```

> Give a stuff

```java

FayUtils.give(ItemStack item, Player player);
FayUtils.give(Player player, ItemStack item);

```

> Json persist

```java

public class Commands implements JsonPersist {
    @Override
    public void loadData() {
        
    }

    @Override
    public void saveData() {

    }
}

```

---

## How to install ?

> All the code required to get started

### Clone

> Buy a license on fayle website (https://fayle.fr)

### Setup

> Required Spigot

> Go in the config.yml in Fayle in your plugins folder and put your token

---
