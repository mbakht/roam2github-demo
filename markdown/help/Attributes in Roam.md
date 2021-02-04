- status:: [[Experimental]]
    - ## Warning: This feature is in alpha, hasn't been fully developed yet.  This is mostly for experimentation
- Blocks and Pages in Roam can both have attributes
    - attributes are formed by wring `::` at the front of a block
        - see "founder of:: [[Roam]]"
    - The structure of an attribute is `Entity Attribute Value`
- When an attribute is at the first level of indentation of a page, it is attached to the page itself
    - see "status:: [[Experimental]]"
- When the block which an attribute is attached to only contains references to other blocks or pages, (or commas or the word and) the attribute is attached to those referenced entities instead
    - ## Example
        - [[Conor]] and [[Josh]]
            - founder of:: [[Roam]]
            - Programming Languages:: [[Clojure]] [[Javascript]]  
        - This setup will create 6 EAV relationships
            - Conor - founder of - Roam
            - Josh -  founder of - Roam
            - Conor - Programming Languages - Clojure 
            - Conor - Programming Languages - Javascript
            - Josh  - Programming Languages - Clojure
            - Josh - Programming Languages - Javascript
- When the block that an attribute is defined on contains only a string, then the value of the string is assigned as the value of the attribute
    - ## Examples
        - [[Conor]]
            - founder of:: [[Localocracy]]
            - age:: 32
        - [[Josh]]
            - age:: 22
- 
- These attributes will eventually have a lot more power in Roam, for now, the only thing they are used for is to generate tables
    - and charts in the limited case of attributes with numerical values that are excuslively placed on Daily Note pages 
- Attribute tables are written as 
    - `{{attr-table:` `[[``Link to attribute``]]``}}` 
    - Example
        - {{attr-table: [[status]]}}
- Attribute tables are "greedy" -- and try to pull in all related attributes that could be relevant to the table
    - Steps
        - They look at the page listed to see if and where  it has been used as an attribute
        - they will look for all of the entities which have the attribute assigned
        - they will then find all of the other attributes which have been associated with those entities, and chart the values of each of those subsequent attributes
    - Example
        - Attribute Table for Age  
            - ## {{attr-table: [[age]]}} 
                - Includes more info than just age
        - ## Attribute Table for Programming Languages {{attr-table: [[Programming Languages]]}}
            - includes more info than just programming languages
- Clicking on the cell of each table will bring you to the place where the attribute was defined
    - The attributes do not need to be all defined in one place to be collected into the table
        - For example, if you click on [[San Francisco]] in either of the above tables, you'll see that the **lives in** relationship was defined on the [[Conor]] page, not near where other attributes were defined. 
- Attributes can themselves be annotated using an [[Associative Data Model]]
- 