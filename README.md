# link
let copy link
git clone
cp npx @angular/cli@20 new practice --ssr=false --route=false
y n n npx ng serve - cd practice - npx ng serve
browser: localhost:4200 cp practice > src > app.html

>app.html = <h1> Practice </h1> 
>source_control >msg = 'tsk1 cmplt' > cmmt > ... > push

>cp > cd practice > npx ng g service shop-service 
> app > new folder ="models" > new file="shop-item.ts"
shop-items.ts = export interface ShopItem{ id:string; modelName: string; price: number; isAvailable: boolean;}
shop-service.ts > export class ShopService { items: ShopItem[] = [ { id:'', modelName: 'Kingston', price:10, isAvailable: true},
{ id:'', modelName: 'modelTwo', price: 20, isAvailable: false}]
google> guidegenerator.com > 2> pst>shop-service.ts>id:''>pst - id 
> source_control> msg='tsk2.1'>push

shop-service.ts > getItems(){return this.items;}
>source_control> msg='tsk2.2'>push

cp > npm install uuid > shop-service.ts > import{v4} from 'uuid';>addItem(tem: ShopItem){item.id=v4();this.items.push(item);return item.id;}
>source_control> msg='tsk2.3'>push

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
