# Router

## Jak přidat routing do aplikace

Do /src/app přidej app-routing.module.ts

```typescript
import { NgModule } from '@angular/core';
import { Routes, RouterModule } from '@angular/router';

const routes: Routes = [
  {
    path: '',
    canActivate: [],
    children: [
      {
        path: 'ngxs',
        loadChildren: () => import('./lazy/ngxs/ngxs.module').then(a => a.NgxsModule)
      }
    ]
  },
  {
    path: '**',
    redirectTo: 'error/page404'
  }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule {}
```



Jsou v něm cesty od root cesty dále, první úroveň. Každá cesta odpovídá jednomu feature modulu.

Importuje se zde routerModule.forRoot(routes). Jenom zde smí být importovaný s konfigurací .forRoot(), jinde ne!

Feature moduly mají zase svoje vlastní routovací moduly. Tam se importuje routerModule.forChild(routes) a jsou tam cesty pro další úrovně. Typicky tam nebývá root cesta '', ale může být. \
Pokud tím úroveň (cesty) končí, tak se komponenty pro cestu odkazují přímo, a ne přes funkci loadChildren. Příklad:\


```typescript
import { NgModule } from '@angular/core';
import { Routes, RouterModule } from '@angular/router';
import { AutomaticEvaluationPageComponent } from './pages/automatic-evaluation-page/automatic-evaluation-page.component';

const routes: Routes = [
  /* begin - test routes */
  {
    path: 'automatic-evaluation',
    component: AutomaticEvaluationPageComponent,
    pathMatch: 'full'
  },
  /* end - test routes */
  {
    path: '**',
    redirectTo: '/error'
  }
];

@NgModule({
  imports: [RouterModule.forChild(routes)],
  exports: [RouterModule]
})
export class ScoringRoutingModule {}
```

