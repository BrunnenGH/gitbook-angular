# ng generate

`ng generate <schematics>`

## module \<name>

_--module_ Do kterého modulu bude importován. Jen jméno bez přípony Module,

_--project_

\--route    Cesta, pokud to je lazy loaded modul. Také se tak dělají lazy loaded feature moduly:\
`ng generate module customers --route customers --module app.module`





_--routing_    Vytvoří modul + k němu routovací modul. Takhle se dobře vytváří lazy loaded feature moduly.

_--routing-scope_    Child nebo Root. Pro Child i Root to vygeneruje jak routovací modul, tak modul který ho používá.  Nevím k čemu to je.





## component \<name>

Má hodně možností, neuvádím všechny.

[https://angular.io/cli/generate#component-command](https://angular.io/cli/generate#component-command)



Aby se vytvořila v místě kde chceš, musíš zadat relativní cesty od /src/app.

`ng generate component lazy/ngxs/Action --module lazy/ngxs --style=scss`
