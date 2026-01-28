# GitHub Copilot Instructions - Angular 21 Projects

## Project Context
Enterprise-grade Angular application with Modular Architecture, Reactive State Management using Signals, and Component-Driven Development with PrimeNG + Tailwind CSS.

## Prerequisites
- Node.js 20+ LTS
- npm 10+ or pnpm 9+
- Angular CLI 21+
- Git
- IDE: VS Code with Angular Language Service, Tailwind CSS IntelliSense, and Copilot extensions

## Technology Stack
- **Angular**: 21.x (with Signals, Zoneless change detection)
- **TypeScript**: 5.7+
- **UI Library**: PrimeNG 19+ (NO Material, NO Bootstrap)
- **Styling**: Tailwind CSS 4.x + PrimeNG Theming
- **Icons**: @hugeicons/angular
- **Fonts**: @fontsource packages
- **i18n**: @ngx-translate/core + @ngx-translate/http-loader
- **State Management**: Angular Signals + RxJS (minimal)
- **Routing**: Angular Router (standalone)
- **Environment**: @ngx-env/builder
- **Mock Server**: json-server + @faker-js/faker

## Architecture Pattern
**Feature-Based Modular Architecture** - Organized by business features with shared infrastructure, standalone components, and signal-based state management.

```
src/
├── app/
│   ├── core/                           # Singleton services, guards, interceptors
│   │   ├── services/                   # Auth, HTTP, notification services
│   │   ├── guards/                     # Route guards
│   │   ├── interceptors/               # HTTP interceptors
│   │   ├── models/                     # Global interfaces/types
│   │   └── utils/                      # Helper functions
│   ├── shared/                         # Reusable components, directives, pipes
│   │   ├── components/                 # Dumb/presentational components
│   │   │   ├── ui/                     # Basic UI components
│   │   │   └── complex/                # Complex PrimeNG-based components
│   │   ├── directives/                 # Custom directives
│   │   ├── pipes/                      # Custom pipes
│   │   └── models/                     # Shared interfaces
│   ├── features/                       # Feature modules
│   │   ├── auth/                       # Authentication feature
│   │   ├── dashboard/                  # Dashboard feature
│   │   └── {feature-name}/             # Other features
│   │       ├── components/             # Feature-specific components
│   │       ├── services/               # Feature services
│   │       ├── models/                 # Feature models
│   │       └── {feature-name}.routes.ts
│   ├── layout/                         # Layout components
│   │   ├── header/
│   │   ├── sidebar/
│   │   └── footer/
│   ├── app.component.ts
│   ├── app.config.ts                   # Application configuration
│   └── app.routes.ts                   # Main routing configuration
├── assets/
│   ├── i18n/                           # Translation files
│   │   ├── en.json
│   │   ├── es.json
│   │   └── pt.json
│   ├── images/
│   └── icons/
├── environments/
├── styles/                             # Global styles
│   ├── _primeng-theme.scss            # PrimeNG theme customization
│   ├── _tailwind-base.scss
│   └── styles.scss                     # Main styles entry
├── mocks/                              # Mock data for development
│   ├── db.json
│   ├── routes.json
│   └── generators/
└── env.d.ts                            # Environment types
```

## Feature Module Structure
```
feature-name/
├── components/
│   ├── feature-list/
│   │   ├── feature-list.component.ts
│   │   ├── feature-list.component.html
│   │   └── feature-list.component.scss
│   ├── feature-detail/
│   └── feature-form/
├── services/
│   └── feature.service.ts
├── models/
│   ├── feature.model.ts
│   └── feature-dto.model.ts
├── guards/
│   └── feature.guard.ts
└── feature.routes.ts
```

## Architecture Diagram

### Clean Architecture + Signals

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                            PRESENTATION LAYER                               │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌───────────┐ │
│  │   Pages   │  │   Smart   │  │   Dumb    │  │  Signals  │  │  Effects  │ │
│  │ (Routed)  │  │Components │  │Components │  │  (State)  │  │(Side Eff.)│ │
│  └─────┬─────┘  └─────┬─────┘  └─────┬─────┘  └─────┬─────┘  └─────┬─────┘ │
└────────┼──────────────┼──────────────┼──────────────┼──────────────┼────────┘
         │              │              │              │              │
         └──────────────┴──────────────┴──────────────┴──────────────┘
                                       │
                                       ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                              FEATURE LAYER                                  │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐             │
│  │  Feature Store  │  │ Feature Service │  │  Feature Guard  │             │
│  │    (Signals)    │  │   (Business)    │  │   (Protection)  │             │
│  └────────┬────────┘  └────────┬────────┘  └────────┬────────┘             │
└───────────┼────────────────────┼────────────────────┼───────────────────────┘
            │                    │                    │
            └────────────────────┴────────────────────┘
                                 │
                                 ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                               CORE LAYER                                    │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐             │
│  │  HTTP Services  │  │  Interceptors   │  │  Global Guards  │             │
│  │   (API Calls)   │  │ (Auth, Error)   │  │  (Auth, Role)   │             │
│  └────────┬────────┘  └────────┬────────┘  └────────┬────────┘             │
└───────────┼────────────────────┼────────────────────┼───────────────────────┘
            │                    │                    │
            └────────────────────┴────────────────────┘
                                 │
                                 ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                              SHARED LAYER                                   │
│  ┌───────────────┐  ┌───────────────┐  ┌───────────────┐  ┌───────────────┐│
│  │   UI Comps    │  │  Directives   │  │     Pipes     │  │    Models     ││
│  │  (PrimeNG)    │  │   (Custom)    │  │   (Custom)    │  │  (Interfaces) ││
│  └───────────────┘  └───────────────┘  └───────────────┘  └───────────────┘│
└─────────────────────────────────────────────────────────────────────────────┘
                                 │
                                 ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                             EXTERNAL SYSTEMS                                │
│  ┌───────────────────────┐  ┌───────────────────────┐                      │
│  │    REST APIs          │  │    WebSocket / SSE    │                      │
│  │  (Spring Backend)     │  │  (Real-time Events)   │                      │
│  └───────────────────────┘  └───────────────────────┘                      │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Data Flow Pattern

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                              UNIDIRECTIONAL DATA FLOW                        │
│                                                                              │
│   ┌──────────┐      ┌──────────┐      ┌──────────┐      ┌──────────┐        │
│   │  USER    │ ──▶  │  ACTION  │ ──▶  │  SIGNAL  │ ──▶  │   VIEW   │        │
│   │  EVENT   │      │ (Method) │      │  UPDATE  │      │  RENDER  │        │
│   └──────────┘      └──────────┘      └──────────┘      └──────────┘        │
│        ▲                                                      │              │
│        └──────────────────────────────────────────────────────┘              │
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                        SIGNAL REACTIVITY                            │   │
│   │                                                                     │   │
│   │   signal()  ───▶  computed()  ───▶  effect()  ───▶  Template        │   │
│   │   (Source)        (Derived)        (Side Effect)     (Binding)      │   │
│   │                                                                     │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

## Code Generation Rules

### 1. STANDALONE COMPONENTS (Angular 21)

**ALWAYS create standalone components** - NO NgModules unless absolutely necessary for legacy integration.

**Component Template:**
```typescript
import { Component, signal, computed, effect, inject } from '@angular/core';
import { CommonModule } from '@angular/common';
import { TranslateModule } from '@ngx-translate/core';
import { HugeiconsModule } from '@hugeicons/angular';
import { ButtonModule } from 'primeng/button';
import { CardModule } from 'primeng/card';

@Component({
  selector: 'app-feature-list',
  standalone: true,
  imports: [
    CommonModule,
    TranslateModule,
    HugeiconsModule,
    ButtonModule,
    CardModule,
  ],
  templateUrl: './feature-list.component.html',
  styleUrl: './feature-list.component.scss',
})
export class FeatureListComponent {
  // Inject services
  private readonly featureService = inject(FeatureService);
  private readonly translateService = inject(TranslateService);

  // Signals for reactive state
  items = signal<Feature[]>([]);
  loading = signal<boolean>(false);
  selectedItem = signal<Feature | null>(null);

  // Computed signals
  filteredItems = computed(() => {
    const items = this.items();
    const selected = this.selectedItem();
    return selected ? items.filter(i => i.category === selected.category) : items;
  });

  itemCount = computed(() => this.items().length);
  hasItems = computed(() => this.itemCount() > 0);

  // Effects for side effects
  constructor() {
    effect(() => {
      console.log('Items changed:', this.items().length);
    });
  }

  // Methods
  loadItems(): void {
    this.loading.set(true);
    this.featureService.getItems().subscribe({
      next: (items) => {
        this.items.set(items);
        this.loading.set(false);
      },
      error: (error) => {
        console.error('Error loading items:', error);
        this.loading.set(false);
      }
    });
  }

  selectItem(item: Feature): void {
    this.selectedItem.set(item);
  }
}
```

**Template with PrimeNG + Tailwind:**
```html
<div class="w-full h-full p-4">
  <!-- Header -->
  <div class="flex items-center justify-between mb-6">
    <h1 class="text-2xl font-bold text-gray-900 dark:text-gray-100">
      {{ 'FEATURE.TITLE' | translate }}
    </h1>
    
    <p-button
      [label]="'COMMON.ACTIONS.ADD' | translate"
      icon="pi pi-plus"
      (onClick)="onAdd()"
      styleClass="p-button-primary">
      <ng-template pTemplate="icon">
        <hugeicon name="plus" size="16" class="mr-2"></hugeicon>
      </ng-template>
    </p-button>
  </div>

  <!-- Loading State -->
  @if (loading()) {
    <div class="flex justify-center items-center h-64">
      <p-progressSpinner></p-progressSpinner>
    </div>
  }

  <!-- Content -->
  @if (!loading() && hasItems()) {
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
      @for (item of filteredItems(); track item.id) {
        <p-card 
          [header]="item.name"
          styleClass="hover:shadow-lg transition-shadow duration-300">
          <ng-template pTemplate="header">
            <img [alt]="item.name" [src]="item.imageUrl" 
                 class="w-full h-48 object-cover" />
          </ng-template>
          
          <p class="text-gray-600 dark:text-gray-400 mb-4">
            {{ item.description }}
          </p>
          
          <ng-template pTemplate="footer">
            <div class="flex gap-2">
              <p-button 
                [label]="'COMMON.ACTIONS.VIEW' | translate"
                icon="pi pi-eye"
                (onClick)="selectItem(item)"
                styleClass="p-button-sm p-button-text" />
              <p-button 
                [label]="'COMMON.ACTIONS.EDIT' | translate"
                icon="pi pi-pencil"
                (onClick)="onEdit(item)"
                styleClass="p-button-sm p-button-text" />
            </div>
          </ng-template>
        </p-card>
      }
    </div>
  }

  <!-- Empty State -->
  @if (!loading() && !hasItems()) {
    <div class="flex flex-col items-center justify-center h-64 text-gray-500">
      <hugeicon name="inbox" size="64" class="mb-4 text-gray-400"></hugeicon>
      <p class="text-lg">{{ 'FEATURE.EMPTY_STATE' | translate }}</p>
    </div>
  }
</div>
```

---

### 2. SIGNALS-BASED STATE MANAGEMENT

**ALWAYS use Signals for local component state** - Avoid unnecessary RxJS complexity.

```typescript
export class ProductService {
  private readonly http = inject(HttpClient);

  // Signal-based cache
  private productsCache = signal<Product[]>([]);
  
  // Public readonly signal
  readonly products = this.productsCache.asReadonly();

  // Computed values
  readonly productCount = computed(() => this.productsCache().length);
  readonly hasProducts = computed(() => this.productCount() > 0);

  loadProducts(): Observable<Product[]> {
    return this.http.get<Product[]>('/api/products').pipe(
      tap(products => this.productsCache.set(products))
    );
  }

  addProduct(product: Product): void {
    this.productsCache.update(products => [...products, product]);
  }

  updateProduct(id: string, updates: Partial<Product>): void {
    this.productsCache.update(products =>
      products.map(p => p.id === id ? { ...p, ...updates } : p)
    );
  }

  removeProduct(id: string): void {
    this.productsCache.update(products =>
      products.filter(p => p.id !== id)
    );
  }
}
```

---

### 3. PRIMENG + TAILWIND INTEGRATION

**PrimeNG Theme Customization with Figma Design Tokens:**

```scss
// styles/_primeng-theme.scss

// Import PrimeNG base styles
@import 'primeng/resources/primeng.min.css';

// Design tokens from Figma (via MCP)
$primary-color: #4F46E5; // indigo-600
$primary-hover: #4338CA; // indigo-700
$primary-active: #3730A3; // indigo-800

$surface-0: #FFFFFF;
$surface-50: #F9FAFB;
$surface-100: #F3F4F6;
$surface-200: #E5E7EB;

$text-color: #111827;
$text-secondary: #6B7280;

// Override PrimeNG CSS variables
:root {
  --primary-color: #{$primary-color};
  --primary-color-text: #FFFFFF;
  --surface-0: #{$surface-0};
  --surface-50: #{$surface-50};
  --surface-100: #{$surface-100};
  --surface-ground: #{$surface-0};
  --text-color: #{$text-color};
  --text-color-secondary: #{$text-secondary};
  
  // Spacing (consistent with Tailwind)
  --inline-spacing: 0.5rem;
  --border-radius: 0.375rem; // rounded-md
  
  // Shadows (Tailwind-compatible)
  --shadow-1: 0 1px 3px 0 rgb(0 0 0 / 0.1);
  --shadow-2: 0 4px 6px -1px rgb(0 0 0 / 0.1);
}

// Dark mode
.dark {
  --surface-0: #1F2937;
  --surface-50: #111827;
  --surface-100: #0F172A;
  --surface-ground: #111827;
  --text-color: #F9FAFB;
  --text-color-secondary: #D1D5DB;
}

// PrimeNG component customization with Tailwind utilities
.p-button {
  @apply font-medium transition-all duration-200;
  
  &.p-button-primary {
    @apply bg-primary-600 hover:bg-primary-700 border-primary-600;
  }
  
  &.p-button-secondary {
    @apply bg-gray-600 hover:bg-gray-700 border-gray-600;
  }
  
  &.p-button-success {
    @apply bg-green-600 hover:bg-green-700 border-green-600;
  }
}

.p-card {
  @apply rounded-lg shadow-md border border-gray-200 dark:border-gray-700;
  @apply bg-white dark:bg-gray-800;
  
  .p-card-title {
    @apply text-xl font-semibold text-gray-900 dark:text-gray-100;
  }
  
  .p-card-content {
    @apply text-gray-600 dark:text-gray-400;
  }
}

.p-datatable {
  @apply rounded-lg overflow-hidden border border-gray-200 dark:border-gray-700;
  
  .p-datatable-thead > tr > th {
    @apply bg-gray-50 dark:bg-gray-900 text-gray-900 dark:text-gray-100;
    @apply font-semibold border-b border-gray-200 dark:border-gray-700;
  }
  
  .p-datatable-tbody > tr {
    @apply hover:bg-gray-50 dark:hover:bg-gray-800 transition-colors;
    
    > td {
      @apply border-b border-gray-100 dark:border-gray-800;
    }
  }
}
```

---

### 4. COMPLEX COMPONENTS WITH PRIMENG

**Reusable Data Table Component:**

```typescript
// shared/components/complex/data-table/data-table.component.ts
import { Component, input, output, signal, computed, ViewChild } from '@angular/core';
import { CommonModule } from '@angular/common';
import { FormsModule } from '@angular/forms';
import { TranslateModule } from '@ngx-translate/core';
import { TableModule, Table } from 'primeng/table';
import { ButtonModule } from 'primeng/button';
import { InputTextModule } from 'primeng/inputtext';
import { MultiSelectModule } from 'primeng/multiselect';
import { HugeiconsModule } from '@hugeicons/angular';

export interface TableColumn {
  field: string;
  header: string;
  sortable?: boolean;
  filterable?: boolean;
  width?: string;
  type?: 'text' | 'number' | 'date' | 'boolean' | 'actions';
}

export interface TableConfig {
  columns: TableColumn[];
  paginator?: boolean;
  rows?: number;
  rowsPerPageOptions?: number[];
  globalFilterFields?: string[];
}

@Component({
  selector: 'app-data-table',
  standalone: true,
  imports: [
    CommonModule,
    FormsModule,
    TranslateModule,
    TableModule,
    ButtonModule,
    InputTextModule,
    MultiSelectModule,
    HugeiconsModule,
  ],
  templateUrl: './data-table.component.html',
  styleUrl: './data-table.component.scss'
})
export class DataTableComponent<T = any> {
  @ViewChild('dt') table!: Table;

  // Inputs
  data = input.required<T[]>();
  config = input.required<TableConfig>();
  loading = input<boolean>(false);
  selectable = input<boolean>(false);

  // Outputs
  onView = output<T>();
  onEdit = output<T>();
  onDelete = output<T>();
  onExport = output<void>();
  onSelectionChange = output<T[]>();

  // Internal state
  selectedColumns = signal<TableColumn[]>([]);
  selectedRows = signal<T[]>([]);
  globalFilterValue = signal<string>('');
  
  // Computed
  columnOptions = computed(() => this.config().columns);
  visibleColumns = computed(() => {
    const selected = this.selectedColumns();
    return selected.length > 0 ? selected : this.config().columns;
  });

  constructor() {
    // Initialize with all columns
    this.selectedColumns.set(this.config().columns);
  }

  onGlobalFilter(event: Event): void {
    const value = (event.target as HTMLInputElement).value;
    this.globalFilterValue.set(value);
    this.table.filterGlobal(value, 'contains');
  }

  clearFilters(): void {
    this.table.clear();
    this.globalFilterValue.set('');
  }

  handleView(rowData: T): void {
    this.onView.emit(rowData);
  }

  handleEdit(rowData: T): void {
    this.onEdit.emit(rowData);
  }

  handleDelete(rowData: T): void {
    this.onDelete.emit(rowData);
  }

  handleExport(): void {
    this.onExport.emit();
  }

  handleSelectionChange(selection: T[]): void {
    this.selectedRows.set(selection);
    this.onSelectionChange.emit(selection);
  }
}
```

**Data Table Template:**

```html
<!-- shared/components/complex/data-table/data-table.component.html -->
<div class="w-full">
  <!-- Toolbar -->
  <div class="flex items-center justify-between mb-4 p-4 bg-white dark:bg-gray-800 rounded-lg shadow-sm">
    <div class="flex items-center gap-4 flex-1">
      <!-- Global Search -->
      @if (config().globalFilterFields) {
        <span class="p-input-icon-left flex-1 max-w-md">
          <hugeicon name="search" size="20" class="text-gray-400 absolute left-3 top-1/2 -translate-y-1/2"></hugeicon>
          <input 
            pInputText 
            type="text" 
            [placeholder]="'COMMON.SEARCH' | translate"
            [value]="globalFilterValue()"
            (input)="onGlobalFilter($event)"
            class="w-full pl-10" />
        </span>
      }
      
      <!-- Column Toggle -->
      <p-multiSelect 
        [options]="columnOptions()"
        [(ngModel)]="selectedColumns"
        optionLabel="header"
        [placeholder]="'TABLE.COLUMNS' | translate"
        [style]="{'min-width': '200px'}"
        display="chip">
      </p-multiSelect>
    </div>
    
    <!-- Actions -->
    <div class="flex gap-2">
      <p-button 
        icon="pi pi-filter-slash"
        [label]="'COMMON.CLEAR_FILTERS' | translate"
        (onClick)="clearFilters()"
        styleClass="p-button-outlined p-button-sm" />
      <p-button 
        [label]="'COMMON.EXPORT' | translate"
        (onClick)="handleExport()"
        styleClass="p-button-sm">
        <ng-template pTemplate="icon">
          <hugeicon name="download" size="16" class="mr-2"></hugeicon>
        </ng-template>
      </p-button>
    </div>
  </div>

  <!-- Table -->
  <p-table 
    #dt
    [value]="data()"
    [columns]="visibleColumns()"
    [paginator]="config().paginator ?? true"
    [rows]="config().rows ?? 10"
    [rowsPerPageOptions]="config().rowsPerPageOptions ?? [10, 25, 50]"
    [globalFilterFields]="config().globalFilterFields"
    [loading]="loading()"
    [rowHover]="true"
    [showCurrentPageReport]="true"
    [(selection)]="selectedRows"
    (selectionChange)="handleSelectionChange($event)"
    currentPageReportTemplate="{{ 'TABLE.PAGE_REPORT' | translate }}"
    styleClass="p-datatable-gridlines"
    responsiveLayout="scroll">
    
    <ng-template pTemplate="header" let-columns>
      <tr>
        @if (selectable()) {
          <th style="width: 4rem">
            <p-tableHeaderCheckbox></p-tableHeaderCheckbox>
          </th>
        }
        
        @for (col of columns; track col.field) {
          <th 
            [pSortableColumn]="col.sortable ? col.field : ''"
            [style.width]="col.width">
            <div class="flex items-center gap-2">
              {{ col.header | translate }}
              @if (col.sortable) {
                <p-sortIcon [field]="col.field"></p-sortIcon>
              }
            </div>
            @if (col.filterable) {
              <p-columnFilter 
                type="text" 
                [field]="col.field" 
                display="menu">
              </p-columnFilter>
            }
          </th>
        }
      </tr>
    </ng-template>

    <ng-template pTemplate="body" let-rowData let-columns="columns">
      <tr [pSelectableRow]="rowData">
        @if (selectable()) {
          <td>
            <p-tableCheckbox [value]="rowData"></p-tableCheckbox>
          </td>
        }
        
        @for (col of columns; track col.field) {
          <td>
            @switch (col.type) {
              @case ('actions') {
                <div class="flex gap-2">
                  <p-button 
                    icon="pi pi-eye"
                    (onClick)="handleView(rowData)"
                    [pTooltip]="'COMMON.ACTIONS.VIEW' | translate"
                    tooltipPosition="top"
                    styleClass="p-button-rounded p-button-text p-button-sm" />
                  <p-button 
                    icon="pi pi-pencil"
                    (onClick)="handleEdit(rowData)"
                    [pTooltip]="'COMMON.ACTIONS.EDIT' | translate"
                    tooltipPosition="top"
                    styleClass="p-button-rounded p-button-text p-button-sm" />
                  <p-button 
                    icon="pi pi-trash"
                    (onClick)="handleDelete(rowData)"
                    [pTooltip]="'COMMON.ACTIONS.DELETE' | translate"
                    tooltipPosition="top"
                    styleClass="p-button-rounded p-button-text p-button-danger p-button-sm" />
                </div>
              }
              @case ('boolean') {
                <i [class]="rowData[col.field] ? 'pi pi-check text-green-500' : 'pi pi-times text-red-500'"></i>
              }
              @case ('date') {
                {{ rowData[col.field] | date:'short' }}
              }
              @default {
                {{ rowData[col.field] }}
              }
            }
          </td>
        }
      </tr>
    </ng-template>

    <ng-template pTemplate="emptymessage">
      <tr>
        <td [attr.colspan]="visibleColumns().length + (selectable() ? 1 : 0)">
          <div class="flex flex-col items-center justify-center py-8 text-gray-500">
            <hugeicon name="inbox" size="64" class="mb-4 text-gray-400"></hugeicon>
            <p class="text-lg">{{ 'TABLE.NO_DATA' | translate }}</p>
          </div>
        </td>
      </tr>
    </ng-template>
  </p-table>
</div>
```

---

### 5. INTERNATIONALIZATION (i18n) WITH @ngx-translate

**Setup:**

```typescript
// app.config.ts
import { ApplicationConfig, importProvidersFrom } from '@angular/core';
import { provideRouter } from '@angular/router';
import { provideHttpClient, withInterceptors } from '@angular/common/http';
import { TranslateModule, TranslateLoader } from '@ngx-translate/core';
import { TranslateHttpLoader } from '@ngx-translate/http-loader';
import { HttpClient } from '@angular/common/http';

export function HttpLoaderFactory(http: HttpClient) {
  return new TranslateHttpLoader(http, './assets/i18n/', '.json');
}

export const appConfig: ApplicationConfig = {
  providers: [
    provideRouter(routes),
    provideHttpClient(withInterceptors([authInterceptor])),
    importProvidersFrom(
      TranslateModule.forRoot({
        defaultLanguage: 'en',
        loader: {
          provide: TranslateLoader,
          useFactory: HttpLoaderFactory,
          deps: [HttpClient]
        }
      })
    )
  ]
};
```

**Translation Files:**

```json
// assets/i18n/en.json
{
  "COMMON": {
    "ACTIONS": {
      "ADD": "Add",
      "EDIT": "Edit",
      "DELETE": "Delete",
      "SAVE": "Save",
      "CANCEL": "Cancel",
      "VIEW": "View",
      "SEARCH": "Search",
      "EXPORT": "Export",
      "CLEAR_FILTERS": "Clear Filters"
    },
    "MESSAGES": {
      "SUCCESS": "Operation completed successfully",
      "ERROR": "An error occurred",
      "CONFIRM_DELETE": "Are you sure you want to delete this item?"
    },
    "LABELS": {
      "NAME": "Name",
      "EMAIL": "Email",
      "PASSWORD": "Password",
      "PHONE": "Phone",
      "ADDRESS": "Address"
    }
  },
  "AUTH": {
    "LOGIN": {
      "TITLE": "Sign In",
      "EMAIL": "Email",
      "PASSWORD": "Password",
      "SUBMIT": "Sign In",
      "FORGOT_PASSWORD": "Forgot password?",
      "NO_ACCOUNT": "Don't have an account?",
      "SIGN_UP": "Sign up"
    },
    "REGISTER": {
      "TITLE": "Create Account",
      "SUBMIT": "Sign Up",
      "HAVE_ACCOUNT": "Already have an account?",
      "SIGN_IN": "Sign in"
    }
  },
  "DASHBOARD": {
    "TITLE": "Dashboard",
    "WELCOME": "Welcome back",
    "STATS": {
      "TOTAL_USERS": "Total Users",
      "TOTAL_SALES": "Total Sales",
      "NEW_ORDERS": "New Orders",
      "REVENUE": "Revenue"
    }
  },
  "TABLE": {
    "COLUMNS": "Columns",
    "PAGE_REPORT": "Showing {first} to {last} of {totalRecords} entries",
    "NO_DATA": "No records found"
  },
  "VALIDATION": {
    "REQUIRED": "This field is required",
    "EMAIL": "Please enter a valid email address",
    "MIN_LENGTH": "Minimum length is {min} characters",
    "MAX_LENGTH": "Maximum length is {max} characters",
    "PATTERN": "Invalid format"
  }
}
```

```json
// assets/i18n/es.json
{
  "COMMON": {
    "ACTIONS": {
      "ADD": "Agregar",
      "EDIT": "Editar",
      "DELETE": "Eliminar",
      "SAVE": "Guardar",
      "CANCEL": "Cancelar",
      "VIEW": "Ver",
      "SEARCH": "Buscar",
      "EXPORT": "Exportar",
      "CLEAR_FILTERS": "Limpiar Filtros"
    },
    "MESSAGES": {
      "SUCCESS": "Operación completada exitosamente",
      "ERROR": "Ocurrió un error",
      "CONFIRM_DELETE": "¿Está seguro de que desea eliminar este elemento?"
    },
    "LABELS": {
      "NAME": "Nombre",
      "EMAIL": "Correo electrónico",
      "PASSWORD": "Contraseña",
      "PHONE": "Teléfono",
      "ADDRESS": "Dirección"
    }
  },
  "AUTH": {
    "LOGIN": {
      "TITLE": "Iniciar Sesión",
      "EMAIL": "Correo electrónico",
      "PASSWORD": "Contraseña",
      "SUBMIT": "Iniciar Sesión",
      "FORGOT_PASSWORD": "¿Olvidó su contraseña?",
      "NO_ACCOUNT": "¿No tiene una cuenta?",
      "SIGN_UP": "Registrarse"
    }
  },
  "TABLE": {
    "COLUMNS": "Columnas",
    "PAGE_REPORT": "Mostrando {first} a {last} de {totalRecords} registros",
    "NO_DATA": "No se encontraron registros"
  }
}
```

**Usage in Components:**

```typescript
import { Component, inject } from '@angular/core';
import { TranslateService, TranslateModule } from '@ngx-translate/core';

@Component({
  selector: 'app-root',
  standalone: true,
  imports: [TranslateModule],
  template: `
    <div>
      <h1>{{ 'AUTH.LOGIN.TITLE' | translate }}</h1>
      <button (click)="changeLanguage('en')">English</button>
      <button (click)="changeLanguage('es')">Español</button>
    </div>
  `
})
export class AppComponent {
  private readonly translate = inject(TranslateService);

  constructor() {
    this.translate.setDefaultLang('en');
    this.translate.use('en');
  }

  changeLanguage(lang: string): void {
    this.translate.use(lang);
  }
}
```

---

### 6. FONTS WITH @fontsource

**Installation:**

```bash
npm install @fontsource/inter @fontsource/roboto-mono
```

**Import in styles.scss:**

```scss
// styles/styles.scss

// Import fonts
@import '@fontsource/inter/400.css';
@import '@fontsource/inter/500.css';
@import '@fontsource/inter/600.css';
@import '@fontsource/inter/700.css';
@import '@fontsource/roboto-mono/400.css';
@import '@fontsource/roboto-mono/700.css';

// Import other styles
@import 'primeng-theme';
@import 'tailwind-base';
```

**Configure in Tailwind:**

```javascript
// tailwind.config.js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./src/**/*.{html,ts}",
  ],
  darkMode: 'class',
  theme: {
    extend: {
      fontFamily: {
        sans: ['Inter', 'system-ui', 'sans-serif'],
        mono: ['Roboto Mono', 'monospace'],
      },
      colors: {
        primary: {
          50: '#EEF2FF',
          100: '#E0E7FF',
          200: '#C7D2FE',
          300: '#A5B4FC',
          400: '#818CF8',
          500: '#6366F1',
          600: '#4F46E5',
          700: '#4338CA',
          800: '#3730A3',
          900: '#312E81',
        }
      }
    },
  },
  plugins: [
    require('tailwindcss-animate')
  ],
}
```

---

### 7. ROUTING (Standalone Components)

**Main Routes:**

```typescript
// app.routes.ts
import { Routes } from '@angular/router';
import { authGuard } from './core/guards/auth.guard';
import { roleGuard } from './core/guards/role.guard';

export const routes: Routes = [
  {
    path: '',
    redirectTo: '/dashboard',
    pathMatch: 'full'
  },
  {
    path: 'auth',
    loadChildren: () => import('./features/auth/auth.routes')
  },
  {
    path: 'dashboard',
    loadChildren: () => import('./features/dashboard/dashboard.routes'),
    canActivate: [authGuard]
  },
  {
    path: 'products',
    loadChildren: () => import('./features/products/products.routes'),
    canActivate: [authGuard]
  },
  {
    path: 'admin',
    loadChildren: () => import('./features/admin/admin.routes'),
    canActivate: [authGuard, roleGuard],
    data: { roles: ['ADMIN'] }
  },
  {
    path: '**',
    loadComponent: () => import('./shared/components/not-found/not-found.component')
      .then(m => m.NotFoundComponent)
  }
];
```

**Feature Routes:**

```typescript
// features/products/products.routes.ts
import { Routes } from '@angular/router';

export default [
  {
    path: '',
    loadComponent: () => import('./components/product-list/product-list.component')
      .then(m => m.ProductListComponent)
  },
  {
    path: 'new',
    loadComponent: () => import('./components/product-form/product-form.component')
      .then(m => m.ProductFormComponent),
    data: { mode: 'create' }
  },
  {
    path: ':id',
    loadComponent: () => import('./components/product-detail/product-detail.component')
      .then(m => m.ProductDetailComponent)
  },
  {
    path: ':id/edit',
    loadComponent: () => import('./components/product-form/product-form.component')
      .then(m => m.ProductFormComponent),
    data: { mode: 'edit' }
  }
] as Routes;
```

---

### 8. SERVICES

**Base HTTP Service with Signals:**

```typescript
// core/services/http-base.service.ts
import { Injectable, inject, signal } from '@angular/core';
import { HttpClient, HttpParams, HttpHeaders } from '@angular/common/http';
import { Observable, tap, catchError, throwError } from 'rxjs';

export interface PaginatedResponse<T> {
  data: T[];
  total: number;
  page: number;
  pageSize: number;
}

export interface QueryParams {
  page?: number;
  pageSize?: number;
  sort?: string;
  order?: 'asc' | 'desc';
  filter?: Record<string, any>;
}

@Injectable({
  providedIn: 'root'
})
export abstract class HttpBaseService<T> {
  protected readonly http = inject(HttpClient);
  protected abstract readonly endpoint: string;
  protected readonly baseUrl = process.env['NG_APP_API_URL'];
  
  protected cache = signal<T[]>([]);
  readonly data = this.cache.asReadonly();

  protected buildParams(params?: QueryParams): HttpParams {
    let httpParams = new HttpParams();
    
    if (params) {
      if (params.page !== undefined) {
        httpParams = httpParams.set('page', params.page.toString());
      }
      if (params.pageSize !== undefined) {
        httpParams = httpParams.set('pageSize', params.pageSize.toString());
      }
      if (params.sort) {
        httpParams = httpParams.set('sort', params.sort);
      }
      if (params.order) {
        httpParams = httpParams.set('order', params.order);
      }
      if (params.filter) {
        Object.entries(params.filter).forEach(([key, value]) => {
          if (value !== null && value !== undefined) {
            httpParams = httpParams.set(key, value.toString());
          }
        });
      }
    }
    
    return httpParams;
  }

  getAll(params?: QueryParams): Observable<T[]> {
    const httpParams = this.buildParams(params);
    
    return this.http.get<T[]>(`${this.baseUrl}${this.endpoint}`, { params: httpParams }).pipe(
      tap(data => this.cache.set(data)),
      catchError(this.handleError)
    );
  }

  getPaginated(params: QueryParams): Observable<PaginatedResponse<T>> {
    const httpParams = this.buildParams(params);
    
    return this.http.get<PaginatedResponse<T>>(
      `${this.baseUrl}${this.endpoint}/paginated`,
      { params: httpParams }
    ).pipe(
      catchError(this.handleError)
    );
  }

  getById(id: string): Observable<T> {
    return this.http.get<T>(`${this.baseUrl}${this.endpoint}/${id}`).pipe(
      catchError(this.handleError)
    );
  }

  create(item: Partial<T>): Observable<T> {
    return this.http.post<T>(`${this.baseUrl}${this.endpoint}`, item).pipe(
      tap(newItem => this.cache.update(items => [...items, newItem])),
      catchError(this.handleError)
    );
  }

  update(id: string, item: Partial<T>): Observable<T> {
    return this.http.put<T>(`${this.baseUrl}${this.endpoint}/${id}`, item).pipe(
      tap(updated => {
        this.cache.update(items =>
          items.map(i => (i as any).id === id ? updated : i)
        );
      }),
      catchError(this.handleError)
    );
  }

  delete(id: string): Observable<void> {
    return this.http.delete<void>(`${this.baseUrl}${this.endpoint}/${id}`).pipe(
      tap(() => {
        this.cache.update(items =>
          items.filter(i => (i as any).id !== id)
        );
      }),
      catchError(this.handleError)
    );
  }

  protected handleError(error: any): Observable<never> {
    console.error('HTTP Error:', error);
    return throwError(() => error);
  }
}
```

**Feature Service:**

```typescript
// features/products/services/product.service.ts
import { Injectable } from '@angular/core';
import { Observable } from 'rxjs';
import { HttpParams } from '@angular/common/http';
import { HttpBaseService } from '@core/services/http-base.service';
import { Product, ProductDto } from '../models/product.model';

@Injectable({
  providedIn: 'root'
})
export class ProductService extends HttpBaseService<Product> {
  protected readonly endpoint = '/products';

  searchProducts(query: string): Observable<Product[]> {
    const params = new HttpParams().set('q', query);
    return this.http.get<Product[]>(`${this.baseUrl}${this.endpoint}/search`, { params });
  }

  getProductsByCategory(categoryId: string): Observable<Product[]> {
    return this.http.get<Product[]>(`${this.baseUrl}${this.endpoint}/category/${categoryId}`);
  }

  getProductsByPriceRange(min: number, max: number): Observable<Product[]> {
    const params = new HttpParams()
      .set('minPrice', min.toString())
      .set('maxPrice', max.toString());
    return this.http.get<Product[]>(`${this.baseUrl}${this.endpoint}/price-range`, { params });
  }

  getFeaturedProducts(): Observable<Product[]> {
    return this.http.get<Product[]>(`${this.baseUrl}${this.endpoint}/featured`);
  }

  updateStock(id: string, quantity: number): Observable<Product> {
    return this.http.patch<Product>(`${this.baseUrl}${this.endpoint}/${id}/stock`, { quantity });
  }
}
```

---

### 9. MODELS & DTOs

```typescript
// features/products/models/product.model.ts

export interface Product {
  id: string;
  name: string;
  description: string;
  price: number;
  categoryId: string;
  category?: Category;
  imageUrl: string;
  images?: string[];
  inStock: boolean;
  stockQuantity: number;
  sku: string;
  tags: string[];
  rating: number;
  reviewCount: number;
  featured: boolean;
  createdAt: Date;
  updatedAt: Date;
}

export interface Category {
  id: string;
  name: string;
  slug: string;
}

export interface ProductDto {
  name: string;
  description: string;
  price: number;
  categoryId: string;
  imageUrl: string;
  images?: string[];
  stockQuantity: number;
  sku: string;
  tags: string[];
  featured?: boolean;
}

export interface ProductFilterDto {
  categoryId?: string;
  minPrice?: number;
  maxPrice?: number;
  inStock?: boolean;
  search?: string;
  tags?: string[];
  featured?: boolean;
  rating?: number;
}

export interface ProductUpdateDto {
  name?: string;
  description?: string;
  price?: number;
  categoryId?: string;
  imageUrl?: string;
  images?: string[];
  stockQuantity?: number;
  tags?: string[];
  featured?: boolean;
}
```

---

### 10. GUARDS

**Auth Guard:**

```typescript
// core/guards/auth.guard.ts
import { inject } from '@angular/core';
import { Router, CanActivateFn } from '@angular/router';
import { AuthService } from '../services/auth.service';

export const authGuard: CanActivateFn = (route, state) => {
  const authService = inject(AuthService);
  const router = inject(Router);
  
  if (authService.isAuthenticated()) {
    return true;
  }
  
  router.navigate(['/auth/login'], {
    queryParams: { returnUrl: state.url }
  });
  return false;
};
```

**Role Guard:**

```typescript
// core/guards/role.guard.ts
import { inject } from '@angular/core';
import { Router, CanActivateFn } from '@angular/router';
import { AuthService } from '../services/auth.service';

export const roleGuard: CanActivateFn = (route, state) => {
  const authService = inject(AuthService);
  const router = inject(Router);
  
  const requiredRoles = route.data['roles'] as string[];
  
  if (!requiredRoles || requiredRoles.length === 0) {
    return true;
  }
  
  const userRoles = authService.getUserRoles();
  const hasRole = requiredRoles.some(role => userRoles.includes(role));
  
  if (hasRole) {
    return true;
  }
  
  router.navigate(['/unauthorized']);
  return false;
};
```

---

### 11. INTERCEPTORS

**Auth Interceptor:**

```typescript
// core/interceptors/auth.interceptor.ts
import { HttpInterceptorFn } from '@angular/common/http';
import { inject } from '@angular/core';
import { AuthService } from '../services/auth.service';

export const authInterceptor: HttpInterceptorFn = (req, next) => {
  const authService = inject(AuthService);
  const token = authService.getToken();
  
  if (token && !req.url.includes('/auth/')) {
    const cloned = req.clone({
      headers: req.headers.set('Authorization', `Bearer ${token}`)
    });
    return next(cloned);
  }
  
  return next(req);
};
```

**Error Interceptor:**

```typescript
// core/interceptors/error.interceptor.ts
import { HttpInterceptorFn, HttpErrorResponse } from '@angular/common/http';
import { inject } from '@angular/core';
import { catchError, throwError } from 'rxjs';
import { MessageService } from 'primeng/api';
import { TranslateService } from '@ngx-translate/core';

export const errorInterceptor: HttpInterceptorFn = (req, next) => {
  const messageService = inject(MessageService);
  const translateService = inject(TranslateService);
  
  return next(req).pipe(
    catchError((error: HttpErrorResponse) => {
      let errorMessage = '';
      
      if (error.error instanceof ErrorEvent) {
        // Client-side error
        errorMessage = error.error.message;
      } else {
        // Server-side error
        switch (error.status) {
          case 400:
            errorMessage = translateService.instant('ERRORS.BAD_REQUEST');
            break;
          case 401:
            errorMessage = translateService.instant('ERRORS.UNAUTHORIZED');
            break;
          case 403:
            errorMessage = translateService.instant('ERRORS.FORBIDDEN');
            break;
          case 404:
            errorMessage = translateService.instant('ERRORS.NOT_FOUND');
            break;
          case 500:
            errorMessage = translateService.instant('ERRORS.SERVER_ERROR');
            break;
          default:
            errorMessage = error.error?.message || translateService.instant('ERRORS.UNKNOWN');
        }
      }
      
      messageService.add({
        severity: 'error',
        summary: translateService.instant('ERRORS.TITLE'),
        detail: errorMessage,
        life: 5000
      });
      
      return throwError(() => error);
    })
  );
};
```

**Loading Interceptor:**

```typescript
// core/interceptors/loading.interceptor.ts
import { HttpInterceptorFn } from '@angular/common/http';
import { inject } from '@angular/core';
import { finalize } from 'rxjs';
import { LoadingService } from '../services/loading.service';

export const loadingInterceptor: HttpInterceptorFn = (req, next) => {
  const loadingService = inject(LoadingService);
  
  loadingService.show();
  
  return next(req).pipe(
    finalize(() => loadingService.hide())
  );
};
```

---

## MCP Configuration

### Install Dependencies

```bash
# Angular Language Service
npm install -g @angular/language-service

# Figma MCP for design tokens
npm install -D @figma/mcp-figma

# Additional tools
npm install -D ts-node nodemon
```

### MCP Configuration File

```json
// .mcp/mcp.json
{
  "mcpServers": {
    "angular-language-service": {
      "command": "node",
      "args": [
        "./node_modules/@angular/language-service/bundles/server.js",
        "--stdio"
      ],
      "capabilities": {
        "completion": true,
        "hover": true,
        "definition": true,
        "references": true,
        "diagnostics": true,
        "codeActions": true,
        "formatting": true
      },
      "settings": {
        "angular": {
          "enable": true,
          "strictTemplates": true
        }
      }
    },
    "figma": {
      "command": "npx",
      "args": ["-y", "@figma/mcp-figma"],
      "env": {
        "FIGMA_ACCESS_TOKEN": "${FIGMA_ACCESS_TOKEN}"
      },
      "capabilities": {
        "designTokens": true,
        "colorExtraction": true,
        "componentMapping": true,
        "spacingExtraction": true,
        "typographyExtraction": true
      },
      "config": {
        "fileKey": "${FIGMA_FILE_KEY}",
        "outputPath": "./src/styles/_design-tokens.scss",
        "tailwindOutputPath": "./tailwind.tokens.js"
      }
    },
    "tailwind-intellisense": {
      "command": "node",
      "args": [
        "./node_modules/tailwindcss-language-server/bin/tailwindcss-language-server",
        "--stdio"
      ],
      "capabilities": {
        "completion": true,
        "hover": true,
        "diagnostics": true,
        "codeActions": true
      },
      "settings": {
        "tailwindCSS": {
          "experimental": {
            "classRegex": [
              "class:\\s*['\"]([^'\"]*)['\"]",
              "className:\\s*['\"]([^'\"]*)['\"]",
              "ngClass:\\s*['\"]([^'\"]*)['\"]"
            ]
          }
        }
      }
    },
    "typescript": {
      "command": "node",
      "args": [
        "./node_modules/typescript/lib/tsserver.js",
        "--stdio"
      ],
      "capabilities": {
        "completion": true,
        "hover": true,
        "definition": true,
        "references": true,
        "diagnostics": true,
        "codeActions": true,
        "formatting": true,
        "rename": true
      }
    }
  }
}
```

---

### Figma Design Token Extraction

**Script to Extract Tokens:**

```typescript
// scripts/extract-figma-tokens.ts
import * as fs from 'fs';
import * as path from 'path';

interface FigmaColor {
  r: number;
  g: number;
  b: number;
  a?: number;
}

interface DesignTokens {
  colors: Record<string, string>;
  spacing: Record<string, string>;
  typography: Record<string, any>;
  borderRadius: Record<string, string>;
  shadows: Record<string, string>;
}

const FIGMA_ACCESS_TOKEN = process.env.FIGMA_ACCESS_TOKEN;
const FIGMA_FILE_KEY = process.env.FIGMA_FILE_KEY;

async function fetchFigmaFile(): Promise<any> {
  const response = await fetch(
    `https://api.figma.com/v1/files/${FIGMA_FILE_KEY}`,
    {
      headers: {
        'X-Figma-Token': FIGMA_ACCESS_TOKEN!
      }
    }
  );
  
  if (!response.ok) {
    throw new Error(`Figma API error: ${response.statusText}`);
  }
  
  return response.json();
}

async function fetchFigmaStyles(): Promise<any> {
  const response = await fetch(
    `https://api.figma.com/v1/files/${FIGMA_FILE_KEY}/styles`,
    {
      headers: {
        'X-Figma-Token': FIGMA_ACCESS_TOKEN!
      }
    }
  );
  
  if (!response.ok) {
    throw new Error(`Figma API error: ${response.statusText}`);
  }
  
  return response.json();
}

function rgbToHex(color: FigmaColor): string {
  const r = Math.round(color.r * 255);
  const g = Math.round(color.g * 255);
  const b = Math.round(color.b * 255);
  return `#${r.toString(16).padStart(2, '0')}${g.toString(16).padStart(2, '0')}${b.toString(16).padStart(2, '0')}`.toUpperCase();
}

function extractTokens(file: any, styles: any): DesignTokens {
  const tokens: DesignTokens = {
    colors: {},
    spacing: {},
    typography: {},
    borderRadius: {},
    shadows: {}
  };
  
  // Extract color styles
  styles.meta.styles
    .filter((style: any) => style.style_type === 'FILL')
    .forEach((style: any) => {
      const node = findNode(file.document, style.node_id);
      if (node?.fills?.[0]?.type === 'SOLID') {
        const colorName = style.name.toLowerCase().replace(/\s+/g, '-').replace(/\//g, '-');
        tokens.colors[colorName] = rgbToHex(node.fills[0].color);
      }
    });
  
  // Extract text styles
  styles.meta.styles
    .filter((style: any) => style.style_type === 'TEXT')
    .forEach((style: any) => {
      const node = findNode(file.document, style.node_id);
      if (node?.style) {
        const typeName = style.name.toLowerCase().replace(/\s+/g, '-').replace(/\//g, '-');
        tokens.typography[typeName] = {
          fontFamily: node.style.fontFamily,
          fontSize: `${node.style.fontSize}px`,
          fontWeight: node.style.fontWeight,
          lineHeight: node.style.lineHeightPx ? `${node.style.lineHeightPx}px` : 'normal',
          letterSpacing: node.style.letterSpacing ? `${node.style.letterSpacing}px` : 'normal'
        };
      }
    });
  
  return tokens;
}

function findNode(node: any, nodeId: string): any {
  if (node.id === nodeId) {
    return node;
  }
  
  if (node.children) {
    for (const child of node.children) {
      const found = findNode(child, nodeId);
      if (found) return found;
    }
  }
  
  return null;
}

function generateSCSSTokens(tokens: DesignTokens): string {
  return `
// Auto-generated from Figma - DO NOT EDIT MANUALLY
// Last updated: ${new Date().toISOString()}

// =============================================================================
// COLORS
// =============================================================================
${Object.entries(tokens.colors).map(([name, value]) => 
  `$color-${name}: ${value};`
).join('\n')}

// =============================================================================
// SPACING
// =============================================================================
${Object.entries(tokens.spacing).map(([name, value]) => 
  `$spacing-${name}: ${value};`
).join('\n')}

// =============================================================================
// TYPOGRAPHY
// =============================================================================
${Object.entries(tokens.typography).map(([name, value]) => 
  `$typography-${name}: (
  font-family: ${value.fontFamily},
  font-size: ${value.fontSize},
  font-weight: ${value.fontWeight},
  line-height: ${value.lineHeight},
  letter-spacing: ${value.letterSpacing}
);`
).join('\n\n')}

// =============================================================================
// BORDER RADIUS
// =============================================================================
${Object.entries(tokens.borderRadius).map(([name, value]) => 
  `$border-radius-${name}: ${value};`
).join('\n')}

// =============================================================================
// SHADOWS
// =============================================================================
${Object.entries(tokens.shadows).map(([name, value]) => 
  `$shadow-${name}: ${value};`
).join('\n')}
  `.trim();
}

function generateTailwindConfig(tokens: DesignTokens): string {
  return `
// Auto-generated from Figma - DO NOT EDIT MANUALLY
// Last updated: ${new Date().toISOString()}

module.exports = {
  theme: {
    extend: {
      colors: ${JSON.stringify(tokens.colors, null, 8)},
      spacing: ${JSON.stringify(tokens.spacing, null, 8)},
      borderRadius: ${JSON.stringify(tokens.borderRadius, null, 8)},
      boxShadow: ${JSON.stringify(tokens.shadows, null, 8)},
    }
  }
};
  `.trim();
}

async function extractAndGenerate(): Promise<void> {
  try {
    console.log('🔍 Fetching Figma file...');
    const file = await fetchFigmaFile();
    
    console.log('🎨 Fetching Figma styles...');
    const styles = await fetchFigmaStyles();
    
    console.log('⚙️  Extracting design tokens...');
    const tokens = extractTokens(file, styles);
    
    console.log('📝 Generating SCSS...');
    const scss = generateSCSSTokens(tokens);
    const scssPath = path.join(__dirname, '../src/styles/_design-tokens.scss');
    fs.writeFileSync(scssPath, scss);
    
    console.log('📝 Generating Tailwind config...');
    const tailwindConfig = generateTailwindConfig(tokens);
    const tailwindPath = path.join(__dirname, '../tailwind.tokens.js');
    fs.writeFileSync(tailwindPath, tailwindConfig);
    
    console.log('✅ Design tokens extracted successfully!');
    console.log(`   - SCSS: ${scssPath}`);
    console.log(`   - Tailwind: ${tailwindPath}`);
  } catch (error) {
    console.error('❌ Error extracting tokens:', error);
    process.exit(1);
  }
}

extractAndGenerate();
```

**Add Scripts to package.json:**

```json
{
  "scripts": {
    "figma:extract": "ts-node scripts/extract-figma-tokens.ts",
    "figma:watch": "nodemon --watch .env --exec npm run figma:extract"
  }
}
```

---

## Environment Configuration

### Install @ngx-env/builder

```bash
npm install @ngx-env/builder --save-dev
```

### Update angular.json

```json
{
  "projects": {
    "your-app": {
      "architect": {
        "build": {
          "builder": "@ngx-env/builder:application",
          "options": {
            "outputPath": "dist/your-app",
            "index": "src/index.html",
            "browser": "src/main.ts",
            "polyfills": ["zone.js"],
            "tsConfig": "tsconfig.app.json",
            "assets": ["src/favicon.ico", "src/assets"],
            "styles": ["src/styles/styles.scss"],
            "scripts": []
          }
        },
        "serve": {
          "builder": "@ngx-env/builder:dev-server",
          "options": {
            "buildTarget": "your-app:build"
          }
        }
      }
    }
  }
}
```

### Environment Files

```bash
# .env (git-ignored)
NG_APP_API_URL=http://localhost:3000/api
NG_APP_ENV=development
NG_APP_FIGMA_ACCESS_TOKEN=your_token_here
NG_APP_FIGMA_FILE_KEY=your_file_key
NG_APP_ENABLE_MOCKS=true

# .env.example (committed to git)
NG_APP_API_URL=http://localhost:3000/api
NG_APP_ENV=development
NG_APP_FIGMA_ACCESS_TOKEN=
NG_APP_FIGMA_FILE_KEY=
NG_APP_ENABLE_MOCKS=true

# .env.production
NG_APP_API_URL=https://api.production.com/api
NG_APP_ENV=production
NG_APP_ENABLE_MOCKS=false
```

### TypeScript Declaration

```typescript
// env.d.ts
declare namespace NodeJS {
  interface ProcessEnv {
    readonly NG_APP_API_URL: string;
    readonly NG_APP_ENV: 'development' | 'staging' | 'production';
    readonly NG_APP_FIGMA_ACCESS_TOKEN: string;
    readonly NG_APP_FIGMA_FILE_KEY: string;
    readonly NG_APP_ENABLE_MOCKS: string;
  }
}
```

### Usage in Code

```typescript
// Access environment variables
const apiUrl = process.env['NG_APP_API_URL'];
const isProduction = process.env['NG_APP_ENV'] === 'production';
const enableMocks = process.env['NG_APP_ENABLE_MOCKS'] === 'true';
```

---

## Mock Server Setup

### Install Dependencies

```bash
npm install -D json-server @faker-js/faker concurrently
```

### Package.json Scripts

```json
{
  "scripts": {
    "start": "ng serve",
    "start:mock": "concurrently \"npm run mock:server\" \"ng serve\"",
    "mock:generate": "node mocks/generators/generate-db.js",
    "mock:server": "json-server --watch mocks/db.json --routes mocks/routes.json --port 3000 --delay 300"
  }
}
```

### Mock Data Generator

```javascript
// mocks/generators/generate-db.js
const { faker } = require('@faker-js/faker');
const fs = require('fs');
const path = require('path');

function generateUsers(count) {
  return Array.from({ length: count }, (_, i) => ({
    id: faker.string.uuid(),
    name: faker.person.fullName(),
    email: faker.internet.email(),
    avatar: faker.image.avatar(),
    role: faker.helpers.arrayElement(['ADMIN', 'USER', 'MANAGER']),
    createdAt: faker.date.past().toISOString(),
    updatedAt: faker.date.recent().toISOString()
  }));
}

function generateProducts(count, categories) {
  return Array.from({ length: count }, (_, i) => ({
    id: faker.string.uuid(),
    name: faker.commerce.productName(),
    description: faker.commerce.productDescription(),
    price: parseFloat(faker.commerce.price({ min: 10, max: 1000 })),
    categoryId: faker.helpers.arrayElement(categories).id,
    imageUrl: faker.image.urlLoremFlickr({ category: 'product' }),
    images: Array.from({ length: 3 }, () => 
      faker.image.urlLoremFlickr({ category: 'product' })
    ),
    inStock: faker.datatype.boolean(),
    stockQuantity: faker.number.int({ min: 0, max: 1000 }),
    sku: faker.string.alphanumeric(8).toUpperCase(),
    tags: Array.from({ length: faker.number.int({ min: 2, max: 5 }) }, () =>
      faker.commerce.productAdjective()
    ),
    rating: parseFloat(faker.number.float({ min: 1, max: 5, precision: 0.1 }).toFixed(1)),
    reviewCount: faker.number.int({ min: 0, max: 500 }),
    featured: faker.datatype.boolean({ probability: 0.2 }),
    createdAt: faker.date.past().toISOString(),
    updatedAt: faker.date.recent().toISOString()
  }));
}

function generateCategories(count) {
  return Array.from({ length: count }, (_, i) => ({
    id: faker.string.uuid(),
    name: faker.commerce.department(),
    slug: faker.helpers.slugify(faker.commerce.department()).toLowerCase()
  }));
}

function generateOrders(count, users, products) {
  return Array.from({ length: count }, (_, i) => ({
    id: faker.string.uuid(),
    userId: faker.helpers.arrayElement(users).id,
    items: Array.from({ length: faker.number.int({ min: 1, max: 5 }) }, () => {
      const product = faker.helpers.arrayElement(products);
      const quantity = faker.number.int({ min: 1, max: 3 });
      return {
        productId: product.id,
        productName: product.name,
        quantity,
        price: product.price,
        total: product.price * quantity
      };
    }),
    status: faker.helpers.arrayElement(['PENDING', 'PROCESSING', 'SHIPPED', 'DELIVERED', 'CANCELLED']),
    total: 0, // Will be calculated
    createdAt: faker.date.past().toISOString(),
    updatedAt: faker.date.recent().toISOString()
  })).map(order => ({
    ...order,
    total: order.items.reduce((sum, item) => sum + item.total, 0)
  }));
}

// Generate data
console.log('🔄 Generating mock data...');

const categories = generateCategories(10);
const users = generateUsers(50);
const products = generateProducts(200, categories);
const orders = generateOrders(100, users, products);

const db = {
  users,
  products,
  categories,
  orders
};

// Write to file
const outputPath = path.join(__dirname, '../db.json');
fs.writeFileSync(outputPath, JSON.stringify(db, null, 2));

console.log('✅ Mock database generated successfully!');
console.log(`   - Users: ${users.length}`);
console.log(`   - Products: ${products.length}`);
console.log(`   - Categories: ${categories.length}`);
console.log(`   - Orders: ${orders.length}`);
console.log(`   - Output: ${outputPath}`);
```

### Routes Configuration

```json
// mocks/routes.json
{
  "/api/v1/*": "/$1",
  "/api/v1/auth/me": "/users/1",
  "/api/v1/products/featured": "/products?featured=true",
  "/api/v1/products/category/:categoryId": "/products?categoryId=:categoryId",
  "/api/v1/users/:id/orders": "/orders?userId=:id"
}
```

---

## Clean Code Best Practices

### 1. Component Responsibilities

**Smart (Container) Components:**
- Inject and use services
- Manage state
- Handle business logic
- Pass data to dumb components
- Handle events from dumb components

**Dumb (Presentational) Components:**
- Receive data via `@Input()`
- Emit events via `@Output()`
- No service injection
- No business logic
- Purely presentational

### 2. Naming Conventions

```typescript
// Components: PascalCase + Component suffix
ProductListComponent
UserFormComponent
DashboardPageComponent

// Services: PascalCase + Service suffix
ProductService
AuthService
NotificationService

// Interfaces: PascalCase (no I prefix)
Product
User
ApiResponse

// DTOs: PascalCase + Dto suffix
CreateProductDto
UpdateUserDto
LoginRequestDto

// Enums: PascalCase
enum UserRole {
  ADMIN = 'ADMIN',
  USER = 'USER',
  MANAGER = 'MANAGER'
}

// Constants: UPPER_SNAKE_CASE
const API_BASE_URL = '...';
const MAX_RETRY_ATTEMPTS = 3;
const DEFAULT_PAGE_SIZE = 20;

// Signals: camelCase
const products = signal<Product[]>([]);
const isLoading = signal(false);
const selectedItem = signal<Product | null>(null);

// Computed: camelCase with descriptive name
const filteredProducts = computed(() => ...);
const hasProducts = computed(() => ...);
const totalPrice = computed(() => ...);

// Methods: camelCase with verb
loadProducts()
deleteUser()
validateForm()
```

### 3. File Organization

```
feature-name/
├── feature-name.component.ts      # Component class
├── feature-name.component.html    # Template
├── feature-name.component.scss    # Styles
└── feature-name.component.spec.ts # Tests
```

### 4. Code Quality Rules

**DO:**
- ✅ Use TypeScript strict mode
- ✅ Always type variables and return types
- ✅ Use immutable data patterns
- ✅ Prefer pure functions
- ✅ Single Responsibility Principle
- ✅ Dependency Injection
- ✅ Signal-based state (when possible)
- ✅ Async/await over nested subscriptions
- ✅ Meaningful variable names
- ✅ Small, focused methods (< 20 lines)
- ✅ Early returns to reduce nesting
- ✅ Use optional chaining (?.)
- ✅ Use nullish coalescing (??)

**DON'T:**
- ❌ Use `any` type (use `unknown` if needed)
- ❌ Business logic in templates
- ❌ Magic numbers/strings
- ❌ Nested subscriptions
- ❌ Side effects in getters
- ❌ Mutable state without signals
- ❌ Long files (> 300 lines)
- ❌ Console.log in production
- ❌ Empty catch blocks
- ❌ Ignoring linter warnings

### 5. Component Example (Good Practices)

```typescript
import { Component, signal, computed, inject, OnInit } from '@angular/core';
import { CommonModule } from '@angular/common';
import { TranslateModule } from '@ngx-translate/core';
import { ProductService } from '../../services/product.service';
import { Product } from '../../models/product.model';

@Component({
  selector: 'app-product-list',
  standalone: true,
  imports: [CommonModule, TranslateModule],
  templateUrl: './product-list.component.html',
  styleUrl: './product-list.component.scss'
})
export class ProductListComponent implements OnInit {
  // Inject services
  private readonly productService = inject(ProductService);
  
  // Signals
  products = signal<Product[]>([]);
  loading = signal(false);
  error = signal<string | null>(null);
  searchQuery = signal('');
  
  // Computed
  filteredProducts = computed(() => {
    const query = this.searchQuery().toLowerCase();
    return query
      ? this.products().filter(p => p.name.toLowerCase().includes(query))
      : this.products();
  });
  
  hasProducts = computed(() => this.filteredProducts().length > 0);
  productCount = computed(() => this.filteredProducts().length);
  
  ngOnInit(): void {
    this.loadProducts();
  }
  
  private loadProducts(): void {
    this.loading.set(true);
    this.error.set(null);
    
    this.productService.getAll().subscribe({
      next: (products) => {
        this.products.set(products);
        this.loading.set(false);
      },
      error: (err) => {
        this.error.set(err.message);
        this.loading.set(false);
      }
    });
  }
  
  onSearch(query: string): void {
    this.searchQuery.set(query);
  }
  
  onRefresh(): void {
    this.loadProducts();
  }
}
```

---

## Testing Best Practices

### Unit Testing Components

```typescript
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { ProductListComponent } from './product-list.component';
import { ProductService } from '../../services/product.service';
import { of, throwError } from 'rxjs';
import { TranslateModule } from '@ngx-translate/core';

describe('ProductListComponent', () => {
  let component: ProductListComponent;
  let fixture: ComponentFixture<ProductListComponent>;
  let productService: jasmine.SpyObj<ProductService>;

  const mockProducts = [
    { id: '1', name: 'Product 1', price: 100 },
    { id: '2', name: 'Product 2', price: 200 }
  ];

  beforeEach(async () => {
    const productServiceSpy = jasmine.createSpyObj('ProductService', ['getAll']);

    await TestBed.configureTestingModule({
      imports: [ProductListComponent, TranslateModule.forRoot()],
      providers: [
        { provide: ProductService, useValue: productServiceSpy }
      ]
    }).compileComponents();

    productService = TestBed.inject(ProductService) as jasmine.SpyObj<ProductService>;
    fixture = TestBed.createComponent(ProductListComponent);
    component = fixture.componentInstance;
  });

  it('should create', () => {
    expect(component).toBeTruthy();
  });

  it('should load products on init', () => {
    productService.getAll.and.returnValue(of(mockProducts));
    
    component.ngOnInit();
    
    expect(component.products()).toEqual(mockProducts);
    expect(component.loading()).toBeFalse();
  });

  it('should handle error when loading products', () => {
    const error = new Error('Failed to load');
    productService.getAll.and.returnValue(throwError(() => error));
    
    component.ngOnInit();
    
    expect(component.error()).toBe(error.message);
    expect(component.loading()).toBeFalse();
  });

  it('should filter products by search query', () => {
    component.products.set(mockProducts);
    
    component.onSearch('Product 1');
    
    expect(component.filteredProducts().length).toBe(1);
    expect(component.filteredProducts()[0].name).toBe('Product 1');
  });
});
```

---

## Icons with HugeIcons

### Why HugeIcons?
- Eliminates manual image management across projects
- No need to duplicate and recolor images for different themes
- Consistent icon styling with Tailwind CSS
- Full dark mode support out of the box
- Better than managing thousands of PNG/SVG files manually

### Installation

```bash
npm install @hugeicons/angular
```

### Basic Usage

```typescript
// In standalone component
import { Component } from '@angular/core';
import { HugeiconsModule } from '@hugeicons/angular';

@Component({
  standalone: true,
  imports: [HugeiconsModule],
  template: `
    <!-- Basic usage -->
    <hugeicon name="home" size="24" class="text-primary"></hugeicon>
    
    <!-- With dark mode support -->
    <hugeicon 
      name="settings" 
      size="20" 
      class="text-gray-600 dark:text-gray-300"
      aria-label="Settings">
    </hugeicon>
    
    <!-- Button with icon -->
    <button class="flex items-center gap-2 px-4 py-2 bg-primary text-white rounded">
      <hugeicon name="plus" size="16"></hugeicon>
      Add Item
    </button>
    
    <!-- Icon with hover state -->
    <hugeicon 
      name="heart" 
      size="24" 
      class="text-gray-400 hover:text-red-500 transition-colors cursor-pointer">
    </hugeicon>
  `
})
export class MyComponent {}
```

### Icon Sizes Standard

| Size | Pixels | Use Case |
|------|--------|----------|
| sm   | 16px   | Inline text, small buttons |
| md   | 20px   | Default buttons, list items |
| lg   | 24px   | Navigation, primary actions |
| xl   | 32px   | Headers, empty states |

### Navigation Example

```typescript
@Component({
  template: `
    <nav class="flex flex-col gap-1">
      @for (item of navItems; track item.route) {
        <a 
          [routerLink]="item.route"
          routerLinkActive="bg-primary/10 text-primary"
          class="flex items-center gap-3 px-4 py-2 rounded-lg text-gray-600 hover:bg-gray-100 dark:text-gray-300 dark:hover:bg-gray-800">
          <hugeicon [name]="item.icon" size="20"></hugeicon>
          <span>{{ item.label }}</span>
        </a>
      }
    </nav>
  `
})
export class NavigationComponent {
  navItems = [
    { icon: 'home-01', label: 'Dashboard', route: '/dashboard' },
    { icon: 'shopping-bag-01', label: 'Products', route: '/products' },
    { icon: 'file-02', label: 'Orders', route: '/orders' },
    { icon: 'users-01', label: 'Customers', route: '/customers' },
    { icon: 'settings-01', label: 'Settings', route: '/settings' },
  ];
}
```

### Alternative: Heroicons
If you prefer Heroicons (maintained by Tailwind team):
- npm: `@heroicons/angular` or `@ng-icons/heroicons`
- Similar API and Tailwind integration

---

## Animations

### Libraries Overview

| Library | Use Case | Complexity |
|---------|----------|------------|
| Tailwind classes | Simple hover/focus states | Low |
| tailwindcss-animate | Enter/exit, common patterns | Low-Medium |
| @angular/animations | State-based, complex sequences | Medium |
| motion / gsap | Gestures, timelines | High |

### Setup tailwindcss-animate

```bash
npm install tailwindcss-animate
```

```javascript
// tailwind.config.js
module.exports = {
  plugins: [
    require('tailwindcss-animate'),
  ],
  theme: {
    extend: {
      animation: {
        'fade-in': 'fadeIn 0.3s ease-out',
        'fade-out': 'fadeOut 0.2s ease-in',
        'slide-up': 'slideUp 0.3s ease-out',
        'slide-down': 'slideDown 0.3s ease-out',
        'scale-in': 'scaleIn 0.2s ease-out',
      },
      keyframes: {
        fadeIn: {
          '0%': { opacity: '0' },
          '100%': { opacity: '1' },
        },
        fadeOut: {
          '0%': { opacity: '1' },
          '100%': { opacity: '0' },
        },
        slideUp: {
          '0%': { transform: 'translateY(10px)', opacity: '0' },
          '100%': { transform: 'translateY(0)', opacity: '1' },
        },
        slideDown: {
          '0%': { transform: 'translateY(-10px)', opacity: '0' },
          '100%': { transform: 'translateY(0)', opacity: '1' },
        },
        scaleIn: {
          '0%': { transform: 'scale(0.95)', opacity: '0' },
          '100%': { transform: 'scale(1)', opacity: '1' },
        },
      },
    },
  },
}
```

### Tailwind Animation Examples

```html
<!-- Fade in on load -->
<div class="animate-fade-in">Content</div>

<!-- Built-in animations -->
<div class="animate-spin">Loading spinner</div>
<div class="animate-pulse">Skeleton loader</div>
<div class="animate-bounce">Bouncing element</div>

<!-- Hover transitions -->
<button class="transition-all duration-200 hover:scale-105 hover:shadow-lg">
  Hover me
</button>

<!-- Card with hover effect -->
<div class="transition-all duration-300 hover:-translate-y-1 hover:shadow-xl">
  Card content
</div>

<!-- Respect reduced motion -->
<div class="motion-safe:animate-fade-in motion-reduce:opacity-100">
  Accessible content
</div>
```

### Angular Animations

```typescript
import { trigger, transition, style, animate, state, query, stagger } from '@angular/animations';

@Component({
  animations: [
    // Enter/Leave animation
    trigger('fadeSlide', [
      transition(':enter', [
        style({ opacity: 0, transform: 'translateY(-10px)' }),
        animate('300ms ease-out', style({ opacity: 1, transform: 'translateY(0)' }))
      ]),
      transition(':leave', [
        animate('200ms ease-in', style({ opacity: 0, transform: 'translateY(-10px)' }))
      ])
    ]),
    
    // State-based animation
    trigger('expandCollapse', [
      state('collapsed', style({ height: '0', overflow: 'hidden' })),
      state('expanded', style({ height: '*' })),
      transition('collapsed <=> expanded', animate('300ms ease-in-out'))
    ]),
    
    // List stagger animation
    trigger('listAnimation', [
      transition('* => *', [
        query(':enter', [
          style({ opacity: 0, transform: 'translateX(-20px)' }),
          stagger(50, [
            animate('300ms ease-out', style({ opacity: 1, transform: 'translateX(0)' }))
          ])
        ], { optional: true })
      ])
    ])
  ],
  template: `
    <!-- Conditional element -->
    @if (showPanel) {
      <div @fadeSlide class="panel">Panel content</div>
    }
    
    <!-- Accordion -->
    <div [@expandCollapse]="isExpanded ? 'expanded' : 'collapsed'">
      Collapsible content
    </div>
    
    <!-- Animated list -->
    <ul [@listAnimation]="items.length">
      @for (item of items; track item.id) {
        <li>{{ item.name }}</li>
      }
    </ul>
  `
})
export class AnimatedComponent {
  showPanel = signal(false);
  isExpanded = signal(false);
  items = signal<Item[]>([]);
}
```

### Loading States

```typescript
@Component({
  template: `
    <!-- Skeleton loader -->
    <div class="animate-pulse space-y-4">
      <div class="h-4 bg-gray-200 rounded w-3/4"></div>
      <div class="h-4 bg-gray-200 rounded w-1/2"></div>
      <div class="h-32 bg-gray-200 rounded"></div>
    </div>
    
    <!-- Spinner with HugeIcons -->
    <div class="flex items-center justify-center">
      <hugeicon name="loading-03" size="24" class="animate-spin text-primary"></hugeicon>
    </div>
    
    <!-- Button loading state -->
    <button [disabled]="isLoading()" class="flex items-center gap-2 px-4 py-2 bg-primary text-white rounded disabled:opacity-50">
      @if (isLoading()) {
        <hugeicon name="loading-03" size="16" class="animate-spin"></hugeicon>
        Processing...
      } @else {
        <hugeicon name="check" size="16"></hugeicon>
        Submit
      }
    </button>
  `
})
export class LoadingComponent {
  isLoading = signal(false);
}
```

---

## Environment Configuration

### Setup @ngx-env/builder

```bash
npm install @ngx-env/builder --save-dev
```

### Update angular.json

```json
{
  "architect": {
    "build": {
      "builder": "@ngx-env/builder:browser",
      "options": { ... }
    },
    "serve": {
      "builder": "@ngx-env/builder:dev-server",
      "options": { ... }
    }
  }
}
```

### Environment Files Structure

```
project-root/
├── .env                    # Local overrides (git-ignored)
├── .env.example            # Template (committed)
├── .env.development        # Development defaults
├── .env.test               # Test environment
├── .env.staging            # Staging environment
├── .env.production         # Production (CI/CD secrets)
└── src/
    └── env.d.ts            # TypeScript declarations
```

### .env.example (Template)

```env
# API Configuration
NG_APP_API_URL=http://localhost:3000/api/v1
NG_APP_WS_URL=ws://localhost:3000

# Environment
NG_APP_ENV=development

# Authentication
NG_APP_AUTH0_DOMAIN=your-domain.auth0.com
NG_APP_AUTH0_CLIENT_ID=your-client-id
NG_APP_AUTH0_AUDIENCE=https://api.yourapp.com

# Feature Flags
NG_APP_FEATURE_NEW_DASHBOARD=false
NG_APP_FEATURE_DARK_MODE=true

# Analytics
NG_APP_GA_TRACKING_ID=
NG_APP_SENTRY_DSN=

# Third Party
NG_APP_STRIPE_PUBLIC_KEY=
NG_APP_MAPS_API_KEY=
```

### TypeScript Declarations (src/env.d.ts)

```typescript
declare namespace NodeJS {
  interface ProcessEnv {
    // API
    NG_APP_API_URL: string;
    NG_APP_WS_URL: string;
    
    // Environment
    NG_APP_ENV: 'development' | 'test' | 'staging' | 'production';
    
    // Auth
    NG_APP_AUTH0_DOMAIN: string;
    NG_APP_AUTH0_CLIENT_ID: string;
    NG_APP_AUTH0_AUDIENCE: string;
    
    // Feature Flags
    NG_APP_FEATURE_NEW_DASHBOARD: string;
    NG_APP_FEATURE_DARK_MODE: string;
    
    // Analytics (optional)
    NG_APP_GA_TRACKING_ID?: string;
    NG_APP_SENTRY_DSN?: string;
    
    // Third Party (optional)
    NG_APP_STRIPE_PUBLIC_KEY?: string;
    NG_APP_MAPS_API_KEY?: string;
  }
}
```

### Environment Service

```typescript
// core/services/environment.service.ts
@Injectable({ providedIn: 'root' })
export class EnvironmentService {
  readonly apiUrl = process.env['NG_APP_API_URL'];
  readonly wsUrl = process.env['NG_APP_WS_URL'];
  readonly env = process.env['NG_APP_ENV'];
  
  readonly isProduction = this.env === 'production';
  readonly isDevelopment = this.env === 'development';
  
  // Feature flags
  readonly features = {
    newDashboard: process.env['NG_APP_FEATURE_NEW_DASHBOARD'] === 'true',
    darkMode: process.env['NG_APP_FEATURE_DARK_MODE'] === 'true',
  };
  
  // Auth config
  readonly auth = {
    domain: process.env['NG_APP_AUTH0_DOMAIN'],
    clientId: process.env['NG_APP_AUTH0_CLIENT_ID'],
    audience: process.env['NG_APP_AUTH0_AUDIENCE'],
  };
}
```

### Usage Examples

```typescript
// In components
@Component({
  template: `
    @if (env.features.newDashboard) {
      <app-new-dashboard />
    } @else {
      <app-legacy-dashboard />
    }
  `
})
export class DashboardComponent {
  env = inject(EnvironmentService);
}

// In services
@Injectable({ providedIn: 'root' })
export class ApiService {
  private readonly env = inject(EnvironmentService);
  private readonly http = inject(HttpClient);
  
  getUsers(): Observable<User[]> {
    return this.http.get<User[]>(`${this.env.apiUrl}/users`);
  }
}
```

### Startup Validation

```typescript
// main.ts
function validateEnvironment(): void {
  const required = [
    'NG_APP_API_URL',
    'NG_APP_ENV',
    'NG_APP_AUTH0_DOMAIN',
    'NG_APP_AUTH0_CLIENT_ID',
  ];
  
  const missing = required.filter(key => !process.env[key]);
  
  if (missing.length > 0) {
    throw new Error(`Missing required environment variables: ${missing.join(', ')}`);
  }
}

validateEnvironment();
bootstrapApplication(AppComponent, appConfig);
```

### .gitignore

```gitignore
# Environment files
.env
.env.local
.env.*.local

# Keep examples
!.env.example
```

---

## Mock Layer with json-server

### Installation

```bash
npm install json-server @faker-js/faker concurrently --save-dev
```

### Folder Structure

```
src/
└── mocks/
    ├── db.json                 # Main mock database
    ├── routes.json             # Custom route mappings
    ├── middlewares/
    │   ├── auth.js             # Mock auth middleware
    │   └── delay.js            # Random delay middleware
    └── generators/
        └── generate-db.js      # Faker-based data generation
```

### Mock Database (src/mocks/db.json)

```json
{
  "users": [
    {
      "id": 1,
      "name": "John Doe",
      "email": "john@example.com",
      "role": "admin",
      "avatar": "https://i.pravatar.cc/150?u=1",
      "createdAt": "2024-01-15T10:30:00Z"
    }
  ],
  "products": [
    {
      "id": 1,
      "name": "Wireless Headphones",
      "description": "High-quality wireless headphones with noise cancellation",
      "price": 199.99,
      "category": "electronics",
      "stock": 50,
      "userId": 1,
      "createdAt": "2024-01-20T14:00:00Z"
    }
  ],
  "categories": [
    { "id": 1, "name": "Electronics", "slug": "electronics" },
    { "id": 2, "name": "Clothing", "slug": "clothing" },
    { "id": 3, "name": "Books", "slug": "books" }
  ]
}
```

### Routes Configuration (src/mocks/routes.json)

```json
{
  "/api/v1/*": "/$1",
  "/auth/me": "/users/1",
  "/auth/login": "/users/1"
}
```

### Data Generator (src/mocks/generators/generate-db.js)

```javascript
const { faker } = require('@faker-js/faker');
const fs = require('fs');

// Generate Users
const generateUsers = (count) => {
  return Array.from({ length: count }, (_, i) => ({
    id: i + 1,
    name: faker.person.fullName(),
    email: faker.internet.email(),
    role: faker.helpers.arrayElement(['admin', 'user', 'editor']),
    avatar: faker.image.avatar(),
    phone: faker.phone.number(),
    address: {
      street: faker.location.streetAddress(),
      city: faker.location.city(),
      country: faker.location.country(),
      zipCode: faker.location.zipCode(),
    },
    createdAt: faker.date.past().toISOString(),
    updatedAt: faker.date.recent().toISOString(),
  }));
};

// Generate Categories
const generateCategories = () => [
  { id: 1, name: 'Electronics', slug: 'electronics', icon: 'cpu' },
  { id: 2, name: 'Clothing', slug: 'clothing', icon: 'shirt' },
  { id: 3, name: 'Books', slug: 'books', icon: 'book' },
  { id: 4, name: 'Home & Garden', slug: 'home-garden', icon: 'home' },
  { id: 5, name: 'Sports', slug: 'sports', icon: 'dumbbell' },
];

// Generate Products
const generateProducts = (count, users, categories) => {
  return Array.from({ length: count }, (_, i) => ({
    id: i + 1,
    name: faker.commerce.productName(),
    description: faker.commerce.productDescription(),
    price: parseFloat(faker.commerce.price({ min: 10, max: 500 })),
    category: faker.helpers.arrayElement(categories).slug,
    stock: faker.number.int({ min: 0, max: 100 }),
    rating: parseFloat(faker.number.float({ min: 3, max: 5, fractionDigits: 1 })),
    images: Array.from({ length: 3 }, () => 
      faker.image.urlLoremFlickr({ category: 'product' })
    ),
    userId: faker.helpers.arrayElement(users).id,
    createdAt: faker.date.past().toISOString(),
  }));
};

// Generate database
const users = generateUsers(50);
const categories = generateCategories();
const products = generateProducts(200, users, categories);

const db = { users, categories, products };

fs.writeFileSync('src/mocks/db.json', JSON.stringify(db, null, 2));
console.log('✅ Mock database generated!');
```

### Package.json Scripts

```json
{
  "scripts": {
    "start": "ng serve",
    "start:mock": "concurrently \"npm run mock:server\" \"ng serve\"",
    "mock:server": "json-server --watch src/mocks/db.json --routes src/mocks/routes.json --port 3000 --delay 300",
    "mock:generate": "node src/mocks/generators/generate-db.js",
    "mock:reset": "npm run mock:generate && npm run mock:server"
  }
}
```

### Service Pattern (Works with Mock and Real API)

```typescript
@Injectable({ providedIn: 'root' })
export class ProductService {
  private readonly apiUrl = process.env['NG_APP_API_URL'];
  private readonly http = inject(HttpClient);
  
  // json-server supports: _page, _limit, _sort, _order, q (search)
  getProducts(params: {
    page?: number;
    limit?: number;
    sort?: string;
    order?: 'asc' | 'desc';
    search?: string;
    category?: string;
  } = {}): Observable<Product[]> {
    let httpParams = new HttpParams();
    
    if (params.page) httpParams = httpParams.set('_page', params.page);
    if (params.limit) httpParams = httpParams.set('_limit', params.limit);
    if (params.sort) httpParams = httpParams.set('_sort', params.sort);
    if (params.order) httpParams = httpParams.set('_order', params.order);
    if (params.search) httpParams = httpParams.set('q', params.search);
    if (params.category) httpParams = httpParams.set('category', params.category);
    
    return this.http.get<Product[]>(`${this.apiUrl}/products`, { params: httpParams });
  }
}
```

### json-server Query Examples

```
// Pagination
GET /products?_page=1&_limit=10

// Sorting
GET /products?_sort=price&_order=desc

// Filtering
GET /products?category=electronics
GET /products?stock_gte=10

// Search
GET /products?q=headphones

// Relationships (embed)
GET /products?_embed=reviews

// Multiple conditions
GET /products?category=electronics&price_lte=200&_sort=rating&_order=desc
```

---

## MCP Server Integration

### IMPORTANT: Query MCP Server for Best Practices

When working on Angular projects, **ALWAYS query the Angular MCP server** for the most up-to-date best practices, guidelines, and patterns.

### Available MCP Servers

Configure the following MCP servers in your project:

```json
// mcp.json
{
  "mcpServers": {
    "angular-cli": {
      "command": "npx",
      "args": ["-y", "@angular/cli", "mcp"],
      "description": "Official Angular CLI MCP - Generate components, services, guards, and follow Angular best practices"
    },
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"],
      "env": {
        "CONTEXT7_API_KEY": "${CONTEXT7_API_KEY}"
      },
      "description": "Context7 - Documentation and context retrieval for libraries (Tailwind, TypeScript, PrimeNG, etc.)"
    }
  }
}
```

### MCP Server Usage

| MCP Server | Use For |
|------------|---------|
| `angular-cli` | Generate components, services, guards, interceptors, pipes. Official Angular patterns and best practices. |
| `context7` | Query documentation for Tailwind CSS, TypeScript, PrimeNG, RxJS, ngx-translate, and other libraries. |

### When to Query MCP

Always query the MCP server when:

1. **Creating new components** - Use `@angular/cli mcp` for latest Angular patterns
2. **Implementing state management** - Signals vs RxJS decisions
3. **Setting up routing** - Guards, resolvers, lazy loading
4. **Configuring forms** - Reactive forms, validation patterns
5. **Implementing animations** - Angular animations best practices
6. **Styling components** - Query Context7 for Tailwind + PrimeNG integration
7. **Writing tests** - Testing patterns and utilities
8. **Performance optimization** - Change detection, lazy loading
9. **Error handling** - Interceptors, global error handling
10. **Accessibility** - ARIA attributes, keyboard navigation

### Query Examples

```bash
# Before creating a component
@mcp-angular What is the recommended pattern for creating a data table component with sorting and pagination in Angular 21?

# Before implementing state
@mcp-angular Should I use Signals or RxJS for managing form state in a multi-step wizard?

# Before styling
@mcp-tailwind What are the best practices for integrating Tailwind with PrimeNG components?

# Before animations
@mcp-angular How to implement stagger animations for list items with @angular/animations?
```

---

## Forbidden Practices

The following practices are **STRICTLY FORBIDDEN** in Angular projects:

### Architecture & Structure
- ❌ **NgModules** for new code (use standalone components)
- ❌ **Circular dependencies** between modules/services
- ❌ **God components** with 500+ lines of code
- ❌ **Business logic in templates** (use computed signals)
- ❌ **Direct DOM manipulation** (use Angular bindings)

### State Management
- ❌ **Nested subscriptions** (use RxJS operators or signals)
- ❌ **Unsubscribed observables** (memory leaks)
- ❌ **Mutable state without signals** (hard to track changes)
- ❌ **Side effects in getters/computed** (unpredictable behavior)
- ❌ **Global mutable variables** (use services with signals)

### Styling & UI
- ❌ **Bootstrap or Material** (use PrimeNG + Tailwind)
- ❌ **Inline styles** (use Tailwind classes or SCSS)
- ❌ **Custom CSS when Tailwind utility exists** (stay consistent)
- ❌ **Manual image icons** (use @hugeicons/angular)
- ❌ **Hardcoded colors** (use design tokens)

### Code Quality
- ❌ **`any` type** (use `unknown` or proper types)
- ❌ **Magic numbers/strings** (use constants or enums)
- ❌ **Empty catch blocks** (always handle errors)
- ❌ **Console.log in production** (use proper logging)
- ❌ **Ignoring linter warnings** (fix or disable with reason)
- ❌ **Skipping i18n** (always use translate pipe)

### Security
- ❌ **Secrets in frontend code** (use environment variables)
- ❌ **Disabling sanitization** without justification
- ❌ **Storing sensitive data in localStorage** (use secure cookies)
- ❌ **Hardcoded API URLs** (use @ngx-env/builder)

### Testing
- ❌ **Skipping tests** for business logic
- ❌ **Testing implementation details** (test behavior)
- ❌ **Mocking everything** (use realistic data)

---

## Recommended Practices

The following practices are **STRONGLY RECOMMENDED** for Angular projects:

### Architecture & Structure
- ✅ **Standalone components** for all new code
- ✅ **Feature-based folder structure** (features/, shared/, core/)
- ✅ **Smart/Dumb component separation** (container/presentational)
- ✅ **Lazy loading** for feature routes
- ✅ **Barrel exports** (index.ts) for shared modules

### State Management
- ✅ **Signals for local state** (components, services)
- ✅ **Computed signals** for derived state
- ✅ **Effects** for side effects (logging, persistence)
- ✅ **RxJS only for HTTP/async** (minimal usage)
- ✅ **Immutable updates** with signal.update()

### Styling & UI
- ✅ **PrimeNG** for complex components (tables, forms, dialogs)
- ✅ **Tailwind CSS** for utility styling
- ✅ **@hugeicons/angular** for all icons
- ✅ **Dark mode support** with Tailwind dark: variants
- ✅ **Design tokens** in tailwind.config.js
- ✅ **tailwindcss-animate** for animations

### Code Quality
- ✅ **TypeScript strict mode** enabled
- ✅ **Explicit return types** on methods
- ✅ **inject()** function over constructor injection
- ✅ **Readonly properties** where applicable
- ✅ **Small focused methods** (< 20 lines)
- ✅ **Early returns** to reduce nesting

### Performance
- ✅ **OnPush change detection** (with signals, automatic)
- ✅ **trackBy** in @for loops (track item.id)
- ✅ **Lazy loading** for routes and heavy components
- ✅ **Virtual scrolling** for large lists (cdk-virtual-scroll)
- ✅ **Image optimization** (lazy loading, WebP)

### Accessibility
- ✅ **Semantic HTML** elements
- ✅ **ARIA labels** for interactive elements
- ✅ **Keyboard navigation** support
- ✅ **prefers-reduced-motion** respect
- ✅ **Color contrast** compliance

### i18n
- ✅ **@ngx-translate** for all text
- ✅ **Translation keys** in SCREAMING_SNAKE_CASE
- ✅ **Organized JSON** by feature (FEATURE.TITLE, FEATURE.ACTIONS.SAVE)
- ✅ **Pluralization** support

### Environment & Config
- ✅ **@ngx-env/builder** for environment variables
- ✅ **Type-safe env access** with env.d.ts
- ✅ **Startup validation** for required variables
- ✅ **.env.example** committed to repository

### Mock & Development
- ✅ **json-server** for mock APIs
- ✅ **@faker-js/faker** for realistic data
- ✅ **Concurrent scripts** for dev + mock server
- ✅ **API contract documentation** in mock files

---

## When Generating Code

### Pre-Generation Checklist

Before generating any code, always:

1. **Query the Angular MCP server** for latest best practices
2. **Check existing patterns** in the codebase
3. **Verify feature location** (features/, shared/, core/)
4. **Confirm dependencies** are installed

### Component Generation Rules

```typescript
// ALWAYS include these imports for components
import { Component, signal, computed, inject } from '@angular/core';
import { CommonModule } from '@angular/common';
import { TranslateModule } from '@ngx-translate/core';
import { HugeiconsModule } from '@hugeicons/angular';

// ALWAYS use standalone: true
@Component({
  standalone: true,
  imports: [CommonModule, TranslateModule, HugeiconsModule, /* PrimeNG modules */],
  // ...
})

// ALWAYS use signals for state
items = signal<Item[]>([]);
loading = signal(false);

// ALWAYS use computed for derived state
filteredItems = computed(() => /* ... */);

// ALWAYS use inject() for services
private readonly service = inject(MyService);
```

### Service Generation Rules

```typescript
// ALWAYS use providedIn: 'root' for singletons
@Injectable({ providedIn: 'root' })
export class MyService {
  // ALWAYS use inject() for dependencies
  private readonly http = inject(HttpClient);
  private readonly env = inject(EnvironmentService);
  
  // ALWAYS use signals for cached state
  private cache = signal<Data[]>([]);
  readonly data = this.cache.asReadonly();
  
  // ALWAYS return Observable from HTTP methods
  loadData(): Observable<Data[]> {
    return this.http.get<Data[]>(`${this.env.apiUrl}/data`).pipe(
      tap(data => this.cache.set(data))
    );
  }
}
```

### Template Generation Rules

```html
<!-- ALWAYS use new control flow -->
@if (loading()) {
  <p-progressSpinner />
}

@for (item of items(); track item.id) {
  <app-item-card [item]="item" />
}

<!-- ALWAYS use translate pipe for text -->
<h1>{{ 'FEATURE.TITLE' | translate }}</h1>

<!-- ALWAYS use HugeIcons for icons -->
<hugeicon name="home" size="24" class="text-primary"></hugeicon>

<!-- ALWAYS use Tailwind for styling -->
<div class="flex items-center gap-4 p-4 bg-white dark:bg-gray-800 rounded-lg shadow">
  ...
</div>
```

### i18n Keys Generation

```json
// ALWAYS organize by feature
{
  "FEATURE_NAME": {
    "TITLE": "Feature Title",
    "DESCRIPTION": "Feature description",
    "ACTIONS": {
      "CREATE": "Create",
      "EDIT": "Edit",
      "DELETE": "Delete",
      "SAVE": "Save",
      "CANCEL": "Cancel"
    },
    "MESSAGES": {
      "SUCCESS": "Operation successful",
      "ERROR": "An error occurred",
      "CONFIRM_DELETE": "Are you sure you want to delete this item?"
    },
    "EMPTY_STATE": "No items found",
    "LOADING": "Loading..."
  }
}
```

### File Naming Conventions

```
# Components
feature-name.component.ts
feature-name.component.html
feature-name.component.scss
feature-name.component.spec.ts

# Services
feature-name.service.ts
feature-name.service.spec.ts

# Models
feature-name.model.ts
feature-name-dto.model.ts

# Guards
feature-name.guard.ts

# Pipes
feature-name.pipe.ts

# Directives
feature-name.directive.ts

# Routes
feature-name.routes.ts
```

---

## Quick Copilot Commands

```bash
# Generate standalone component
@workspace /new Create standalone component for product-list in features/products/components with PrimeNG DataTable, HugeIcons, i18n, and Tailwind styling

# Generate service with signals
@workspace /new Create product service extending HttpBaseService with signal-based cache and all CRUD operations

# Generate complex form component
@workspace /new Create product-form component with PrimeNG form controls, reactive forms, validation, and i18n

# Generate guard
@workspace /new Create role-based auth guard checking for admin role with redirect to unauthorized page

# Generate interceptor
@workspace /new Create error interceptor for global error handling with PrimeNG toast notifications and i18n

# Extract Figma tokens
@workspace /new Create script to extract design tokens from Figma and generate SCSS + Tailwind config

# Generate mock data
@workspace /new Create Faker-based generator for 100 products with realistic data including images, categories, and pricing

# Generate reusable data table
@workspace /new Create reusable data-table component with PrimeNG Table, sorting, filtering, pagination, column toggle, and actions

# Generate auth service
@workspace /new Create authentication service with JWT, login, logout, token refresh, and role management using signals

# Generate layout component
@workspace /new Create main layout component with PrimeNG Sidebar, header, footer, and responsive design
```

---

## Project Setup Checklist

### Initial Setup

```bash
# 1. Create new Angular project
ng new my-app --standalone --routing --style=scss

# 2. Install dependencies
npm install primeng primeicons
npm install @hugeicons/angular
npm install @ngx-translate/core @ngx-translate/http-loader
npm install @fontsource/inter @fontsource/roboto-mono
npm install @ngx-env/builder --save-dev
npm install -D json-server @faker-js/faker concurrently
npm install -D tailwindcss postcss autoprefixer tailwindcss-animate
npm install -D @angular/language-service
npm install -D @figma/mcp-figma ts-node nodemon

# 3. Initialize Tailwind
npx tailwindcss init

# 4. Create folder structure
mkdir -p src/app/{core,shared,features,layout}
mkdir -p src/app/core/{services,guards,interceptors,models,utils}
mkdir -p src/app/shared/{components,directives,pipes,models}
mkdir -p src/app/shared/components/{ui,complex}
mkdir -p src/assets/i18n
mkdir -p src/styles
mkdir -p mocks/generators
mkdir -p scripts
mkdir -p .mcp

# 5. Create configuration files
touch .env .env.example .env.production
touch src/env.d.ts
touch mocks/db.json mocks/routes.json
touch scripts/extract-figma-tokens.ts
touch .mcp/mcp.json
touch src/styles/_primeng-theme.scss
touch src/styles/_tailwind-base.scss
```

### Configuration Files

Update the following files according to the sections above:
1. `angular.json` - Update to use @ngx-env/builder
2. `tailwind.config.js` - Configure Tailwind with PrimeNG
3. `tsconfig.json` - Enable strict mode
4. `package.json` - Add scripts for mock server and Figma extraction
5. `.eslintrc.json` - Configure ESLint
6. `.prettierrc.json` - Configure Prettier
7. `.gitignore` - Add .env files

---

## ESLint + Prettier Configuration

```json
// .eslintrc.json
{
  "root": true,
  "ignorePatterns": ["projects/**/*"],
  "overrides": [
    {
      "files": ["*.ts"],
      "extends": [
        "eslint:recommended",
        "plugin:@typescript-eslint/recommended",
        "plugin:@angular-eslint/recommended",
        "plugin:@angular-eslint/template/process-inline-templates",
        "prettier"
      ],
      "rules": {
        "@angular-eslint/directive-selector": [
          "error",
          { "type": "attribute", "prefix": "app", "style": "camelCase" }
        ],
        "@angular-eslint/component-selector": [
          "error",
          { "type": "element", "prefix": "app", "style": "kebab-case" }
        ],
        "@typescript-eslint/no-explicit-any": "error",
        "@typescript-eslint/explicit-function-return-type": "warn",
        "@typescript-eslint/no-unused-vars": ["error", { "argsIgnorePattern": "^_" }],
        "no-console": ["warn", { "allow": ["warn", "error"] }],
        "prefer-const": "error",
        "no-var": "error"
      }
    },
    {
      "files": ["*.html"],
      "extends": [
        "plugin:@angular-eslint/template/recommended",
        "plugin:@angular-eslint/template/accessibility"
      ],
      "rules": {
        "@angular-eslint/template/no-negated-async": "error",
        "@angular-eslint/template/use-track-by-function": "error"
      }
    }
  ]
}
```

```json
// .prettierrc.json
{
  "singleQuote": true,
  "trailingComma": "es5",
  "printWidth": 100,
  "tabWidth": 2,
  "semi": true,
  "bracketSpacing": true,
  "arrowParens": "always",
  "endOfLine": "lf",
  "overrides": [
    {
      "files": "*.html",
      "options": {
        "parser": "angular"
      }
    }
  ]
}
```

---

## Summary

This comprehensive guide provides everything needed for Angular 21 development:

✅ **Architecture**: Feature-based modular architecture with standalone components  
✅ **State Management**: Signals-first approach with minimal RxJS  
✅ **UI Framework**: PrimeNG + Tailwind CSS integration  
✅ **Icons**: @hugeicons/angular implementation (no manual images)  
✅ **Animations**: tailwindcss-animate + @angular/animations  
✅ **Fonts**: @fontsource management  
✅ **i18n**: @ngx-translate setup with multiple languages  
✅ **Environment**: @ngx-env/builder for .env support  
✅ **Mock Server**: json-server with Faker.js for development  
✅ **MCP Integration**: Angular, TypeScript, Tailwind, and Figma MCPs  
✅ **Design Tokens**: Figma token extraction and integration  
✅ **Clean Code**: Best practices, naming conventions, and patterns  
✅ **Forbidden Practices**: Clear list of what NOT to do  
✅ **Recommended Practices**: Clear list of what TO do  
✅ **Code Generation Rules**: Consistent patterns for all code  
✅ **Testing**: Unit testing strategies  
✅ **Tooling**: ESLint, Prettier, and development workflows  

**IMPORTANT**: Always query the MCP server for Angular best practices before generating code.

**Follow these guidelines for consistent, maintainable, and high-quality Angular applications.**

---

## Additional Resources

- [Angular Documentation](https://angular.dev)
- [Angular Signals Guide](https://angular.dev/guide/signals)
- [PrimeNG Documentation](https://primeng.org)
- [Tailwind CSS Documentation](https://tailwindcss.com)
- [HugeIcons](https://hugeicons.com)
- [@ngx-translate](https://github.com/ngx-translate/core)
- [Figma API Documentation](https://www.figma.com/developers/api)

---

**Version**: 1.0.0  
**Last Updated**: 2026-01-13  
**Angular Version**: 21.x  
**Maintained by**: Your Development Team
