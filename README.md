# Text-Based-GUI
Creates a menu in payday 2


An orgenized simple GUI for various reasons, menu can search from all sub contents, panel is draggable, allows a sliders, toggle buttons and changing panel colors. It doesn't depend on any mods to work. Menu is fixed size to 1280x720 in all resolutions to minimize testing and bugs. Semi support arrow keys to navigate menu, use mouse wheel to change sliders and esc key for quick exit menu. Main button panels and sub panels are scrollable with mouse wheel.


Example on how to initialize the file:
`dofile("mods/mod name/NewSystemMenu.luac")`

or

`local path = "mods/mod name/NewSystemMenu.luac"
local NewSystemMenu = loadstring(io.open(path , "rb"):read("*all"), path)`


Example on how to open the menu after initialize:

```local panel = {
    panel_data = {
        title = "Test Menu",
        main_color = {0.3, 0, 0, 0},
        sub_color = {0.7, 0, 0, 0},
        deselect_color = {1, 0.5, 0.5, 0.5},
        select_color = {1, 0.30196078431372547, 0.7764705882352941, 1}
    },
    {
        name = "Button name",
        description = "",
        callback = function(value)  end,
		focus_callback = function(value)  end,
        hide_in = "menu",
        buttons = {
            {name = "toggle", toggle = true, callback = function(value)  end, description = "A toggle button."},
            {name = "toggle2", toggle = true, callback = function(value)  end},
            {name = "Slider", steps = {1, 13, 100}, callback = function(value)  end},
            {name = "Execute", callback = function(value)  end},
            {name = "Cancel", cancel = true, callback = function(value)  end, focus_callback = function(value)  end}
        }
    },
	{
        name = "Cancel",
        description = "Closes menu.",
        cancel = true
    }
}

local instance, instances = NewSystemMenu:create_menu(panel, "menu id")```


All button arguments are optional and customizable. Screenshot uses this layout.
Hide button in either a menu or game state since some functions should only work in a spesific state.

`hide_in = "menu"
hide_in = "game"`


Defined colors have alpha as first argument then r, g, b.

`main_color = {0.3, 0, 0, 0}`

Callback and focus_callback are same as default dialog menu, they both return values, states of the buttons or indexes.


Useful functions to call:

`instance:get_menus() -- returns all existing menus in a table, also from "instances".
instance:get_menu(menu_id) -- returns your menu table
instance:disable_menu() -- closes the menu
instance:enable_menu() -- opens the menu
instance:enabled() -- returns true or false
instance:create_menu(panel, menu_id) -- creates the menu and opens it`
