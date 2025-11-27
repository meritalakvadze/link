models>new file="item-filter.ts">export interface ItemFilter{model?: string | null;
priceFrom?: number | null; priceTo?: number | null;}
>shop-service.ts > filterItems(filter: ItemFilter){ let result = this.items; if(filter.model !== null && filter.model !== undefined && filter.model !== ''){
result = result.filter(c => c.modelName.includes(filter.model!));
}  if (filter.priceFrom !== null && filter.priceFrom !== undefined){ result = result.filter( c => c.price >= filter.priceFrom!);}
if(filter.priceTo !== null && filter.priceTo !== undefined){ result = result.filter(c = > c.price <= filter.priceTo!);}
return result;} 
> source_control> msg='tsk2.4'>push

cp > npx ng g c usb-search >usb-search.html= <h3>usb flash drive search </h3> >app.ts > imports[UsbSearch] > app.html = <app-usb-search></app-usb-search> >usb-search.ts > UsbSearch> 'seachResults = signal<ShopItem{}>([]);'>usb_search.html = <table class="search-results"> <thead><th>ID</th><th>Model</th><th>Price</th><th>is available/th></thead></table>
<tbody> @for(item of searchResults(): track item.id){ <tr [class]="{ ' out-of-stock' : !item.isAvailable }" > <td>{{item.id}}<td><td>{{item.modelName}}</td><td>@if(item.isAvailable){<span>{{item.price}}GEL</span} else{N/A} </td><td>{{item.isAvailable ? 'Yes' : 'No' }}
>usb-search.css= out-of-sock{ background-color: yellow;}
>usb-search.ts> usbsearch >shopService = inject(ShopService);> add 'implements OnInit' to the 'export calss UsbSearch' > usbsearch > searchForm=new From=Group({model:new FormControl(''), priceFrom: new FormControl<number | null>(null), priceTo: new FormControl<number | null>(null)}); < ngOnInit():void { let allItems = this.shopService.getItems(); this.searchResults.set(allItems)};
>usb-search.ts>@component >imports[]=[ReactiveFormsModule]
>usb-search.css > .search-results{border-collapse:collapse;} .search-results th, .search-results td{ padding: 5px; border: solid 1px; text-align: center;
>usb-search.html > <form [formGroup]="searchForm"><div class="search-filter"><div class="filter-item"><input type="text" formControlname="model" placeholder="Model"/></div><div class="filter-item"><input type="number" formControlname="priceFrom" placeholder="Price from"/></div><div class="filter-item"><input type="number" formControlname="priceTo" placeholder="Price to"/></div><div class="filter-item"><button>Search</button></div><div class="filter-item><button>Reset</button></div>
>usb-search.css> .search-filter{ display: flex; padding-bottom: 5px;} .filter-item{padding-right: 5px;
>source-control>msg='tsk3.2 and tsk3.1'<push

>usb-search.ts > OnSearch(){ let filter = this.searchForm.value; let filteredItems = this.shopService.filterItems({ model: filter.model, priceFrom: filter.priceFrom, priceTo: filter.priceTo}); this.searchResults.set(filteredItems);}
>usb-search.html > <button (click)="onSearch()">Search</button> 
>source-control>msg='tsk3.3'<push

>usb-search.ts > onReset(){  this.searchForm.reset(); let allItems = this.shopService.getItems(); this.searchResults.set(allItems);}-
>usb-search.html > <button (click)="onReset()">Rese</button> 
>source-control>msg='tsk3.4'<push

>cp >npx ng g c add-item 
>app.ts > @component < [UsbSearch, AddItem] < import {AddItem} from './add-item/add-item';
>app.html >  <app-add-item></app-add-item>
>app 
>add-item.html > <h3> Add usb flash drive </h3>
>add-item.ts >imports: [ReactiveFormsModule] >import {ReactiveFormsModule} from '@angular/forms'; export class AddItem{
 form= new formGroup({ modelName new formControl('',[ validators.required, validators.minLength(3), validators.maxLength(50)]), price: new formControl<number | null>(null, [validators.required, validators.min(8)]), isAailable new formControl(false)  });
>add-item.html > <form [formGroup]="form"> <div class="form-item"><input type="text" formControlName="modelName" placeholder="Model Name"/></div>
<div class="form-item"><input type="number" formControlName="price" placeholder="price"/></div>
<div class="form-item"><label for="chk-isAvailable">is available</label><input type="checkbox" formControlName="isAvailable" id="chk-isAvailable"/></div>
<div class="form-item"><button type="submit">Add</button></div>
>add-item.css > .form-item{padding-bottom:5px;}
>source-control>msg='tsk4.1'<push
