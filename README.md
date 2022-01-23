# Finder

Find Instances with conditions, and perform action on them!

## API Reference

### `Finder.find(target: {Instance}, condition: Condition, behavior: Behavior?): {Instance}|any?`

Performs a search on the specified Instances with the `condition`, returns a table of Instances if the `condition` returned true.

If `behavior` is supplied, returns the result from `behavior`.

### `Finder.addTemplate(category: string, name: string, condition: Condition): boolean`

Adds a new template to Finder with the specified category and name. If the name exists in the specified category already, Finder will not add the template and returns `false` with a warn.

If the specified category does not exist, Finder will create the category manually.

### `Finder.getTemplate(category: string, name: string): Condition`

Returns the specified template. If the category or the template name does not exist in the specified category, returns a dummy `Condition` that returns `false`, with a warn.

## Template treeview
```lua
local Finder = {
    Templates = {
        CategoryName = {
            TemplateName: Condition = function(object: Instance): boolean
                return object ~= nil
            end
        }
    }
}
```

## Types
```lua
export type Condition = (object: Instance) -> (boolean)
export type Behavior = (result: {Instance}) -> ()
```