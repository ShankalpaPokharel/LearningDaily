## Tailwind CSS and Dynamic Classes

Dynamic Class Names: Tailwind CSS relies on a <b>predefined set of classes that are included in the build process</b>. If you're trying to use dynamic values for Tailwind classes (e.g., className={bg-${color}-500}), Tailwind may not recognize these classes because they are not explicitly included in your configuration. Tailwind's purge mechanism might also remove these dynamically generated classes from the final build if they are not present in the source files it scans.

## Infinite scrolling

```html
<h1>Financial Company</h1>
<div class="stock-ticker">
    <ul>
        <div class="w-40 h-40 bg-red-500 mr-2"></div>
        <div class="w-40 h-40 bg-blue-500 mr-2"></div>
        <div class="w-40 h-40 bg-green-500 mr-2"></div>
        <div class="w-40 h-40 bg-yellow-500 mr-2"></div>
        <div class="w-40 h-40 bg-purple-500 mr-2"></div>
        <div class="w-40 h-40 bg-pink-500 mr-2"></div>
        <div class="w-40 h-40 bg-orange-500 mr-2"></div>
        <div class="w-40 h-40 bg-teal-500 mr-2"></div>
        <div class="w-40 h-40 bg-indigo-500 mr-2"></div>
        <div class="w-40 h-40 bg-gray-500 mr-2"></div>
    </ul>

    <ul>
        <div class="w-40 h-40 bg-red-500 mr-2"></div>
        <div class="w-40 h-40 bg-blue-500 mr-2"></div>
        <div class="w-40 h-40 bg-green-500 mr-2"></div>
        <div class="w-40 h-40 bg-yellow-500 mr-2"></div>
        <div class="w-40 h-40 bg-purple-500 mr-2"></div>
        <div class="w-40 h-40 bg-pink-500 mr-2"></div>
        <div class="w-40 h-40 bg-orange-500 mr-2"></div>
        <div class="w-40 h-40 bg-teal-500 mr-2"></div>
        <div class="w-40 h-40 bg-indigo-500 mr-2"></div>
        <div class="w-40 h-40 bg-gray-500 mr-2"></div>
    </ul>
</div>
```

```css
.stock-ticker {
    font-size: 15px;
    padding-block: 8px;
    border-block: 1px solid;
    overflow: hidden;
    user-select: none;

    --gap: 20px;
    display: flex;
    gap: var(--gap);
}

.stock-ticker ul {
    list-style: none;
    flex-shrink: 0;
    min-width: 100%;
    display: flex;

    animation: scroll 20s linear infinite;
}

.stock-ticker:hover ul {
    animation-play-state: paused;
}

@keyframes scroll {
    to {
        transform: translateX(calc(-100% - var(--gap)));
    }
}
```

line clamp for limit the maximum line

<p className='marcellus line-clamp-1 px-4 text-xl text-left w-full'>{product.title}</p>

<div className="overflow-hidden  h-[300px] md:h-auto">
    <div className=" md:flex overflow-hidden items-center md:py-2 md:gap-5 justify-between ">
        <ul className="md:flex min-w-full flex-shrink-0  scroll-container items-center gajustify-between">
            {companies.map((company, index) => (
                <div key={index} className="flex-shrink-0 mt-3 md:my-auto md:mr-5 ">
                    <Image className="w-32 rounded-md" src={`/trustedCompanies/${company.p`} alt="logo" height={100} width={100} />
                </div>
            ))}
        </ul>
        <ul className="md:flex min-w-full flex-shrink-0 scroll-container items-center gajustify-between">
            {companies.map((company, index) => (
                <div key={index} className="flex-shrink-0 mt-3 md:my-auto md:mr-5 ">
                    <Image className="w-32 rounded-md" src={`/trustedCompanies/${company.p`} alt="logo" height={100} width={100} />
                </div>
            ))}
        </ul>
    </div>
</div>
</div>

/_ Vertical scroll animation _/
.animate-scroll-vertical {
animation: scroll-vertical 20s linear infinite;
}

@keyframes scroll-vertical {
0% {
transform: translateY(0);
}
100% {
transform: translateY(-100%);
}
}

/_ Apply horizontal scrolling for large devices _/
@media (min-width: 768px) {
.scroll-container {
/_ Use horizontal scroll animation _/
animation: scroll 20s linear infinite;
}
}

/_ Apply vertical scrolling for small devices _/
@media (max-width: 767px) {
.scroll-container {
/_ Use vertical scroll animation _/
animation: scroll-vertical 20s linear infinite;
}
}
