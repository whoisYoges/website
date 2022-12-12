+++
title = "Browsers Comparison"
description = "Comparison, my preference and recommendation of programs"
page_template = "page.html"
[extra]
opengraph = "/assets/images/programs/browsers/browsers.jpg"
comparison = true
+++

<table>
    <caption>Web Browsers</caption>
    <thead>
    <tr class="purple-bg">
        <th scope="col">Name</th>
        <th scope="col">Anti-privacy features</th>
        <th scope="col">Default search engine</th>
        <th scope="col">Code</th>
        <th scope="col">Additional features</th>
        <th scope="col">Chromium based</th>
        <th scope="col">Summary</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td data-label="Name"><a href="https://www.mozilla.org/en-GB/firefox/">Mozilla Firefox</a></td>
        <td data-label="Anti-privacy features" class="red-bg"><span>Telemetry and phoning home is enabled by default, altough most of them can be disabled in about:config.</span></td>
        <td data-label="Default search engine" class="red-bg"><span>Google</span></td>
        <td data-label="Code" class="green-bg"><span>MPL-2.0</span></td>
        <td data-label="Additional features">Tracker blocking</td>
        <td data-label="Chromium based">No</td>
        <td data-label="Summary" class="red-bg"><span>I haven't found a way to disable every request that Firefox makes trough about:config. Avoid.</span></td>
    </tr>
    <tr>
        <td scope="row" data-label="Name"><a href="https://www.google.com/intl/en_uk/chrome/">Google Chrome</a></td>
        <td data-label="Anti-privacy features" class="red-bg"><span>Telemetry, phoning home and additional spyware features are enabled by default and it can't be disabled. Made by one of the biggest tech companies for the cattle for massive data collection.</span></td>
        <td data-label="Default search engine" class="red-bg"><span>Google</span></td>
        <td data-label="Code" class="red-bg"><span>Proprietary</span></td>
        <td data-label="Additional features">-</td>
        <td data-label="Chromium based">Yes</td>
        <td data-label="Summary"class="red-bg"><span>AVOID AT ALL COST!!!</span></td>
    </tr>
    <tr>
        <td scope="row" data-label="Name"><a href="https://www.microsoft.com/en-us/edge">Microsoft Edge</a></td>
        <td data-label="Anti-privacy features" class="red-bg"><span>Telemetry, phoning home and additional spyware features are enabled by default and it can't be disabled. Microsoft's horrible Chromium based spyware.</span></td>
        <td data-label="Default search engine" class="red-bg"><span>Bing</span></td>
        <td data-label="Code" class="red-bg"><span>Proprietary</span></td>
        <td data-label="Additional features">-</td>
        <td data-label="Chromium based"> Yes</td>
        <td data-label="Summary" class="red-bg"><span>Avoid at all cost</span></td>
    </tr>
    <tr>
        <td scope="row" data-label="Name"><a href="https://www.opera.com/">Opera / Opera GX</a></td>
        <td data-label="Anti-privacy features" class="red-bg"><span>Sponsored multiple YouTubers and websites to shill their spyware. Telemetry, phoning home and additional spyware features are enabled by default and it can't be disabled. Owned by a Chinese consortium since 2016 (Golden Brick Capital Private Equity Fund I Limited Partnership). Had a shady past.</span></td>
        <td data-label="Default search engine" class="red-bg"><span>Google</span></td>
        <td data-label="Code" class="red-bg"><span>Proprietary</span></td>
        <td data-label="Additional features">Free Opera VPN which is probably used to harvest user data</td>
        <td data-label="Chromium based">Yes</td>
        <td data-label="Summary" class="red-bg"><span>Chinese spyware, avoid</span></td>
    </tr>
    <tr>
        <td scope="row" data-label="Name"><a href="https://brave.com/">Brave</a></td>
        <td data-label="Anti-privacy features" class="red-bg"><span>Makes requests on startup. They had a "bug" in the past that leakead IPs of those who used the built in Tor window. They did URL injection in the past to earn money via referral programs.</span></td>
        <td data-label="Default search engine" class="yellow-bg"><span>Brave Search</span></td>
        <td data-label="Code" class="green-bg"><span>MPL-2.0</span></td>
        <td data-label="Additional features">Tracker and ad blocking, built in Tor window</td>
        <td data-label="Chromium based">Yes</td>
        <td data-label="Summary" class="red-bg"><span>Avoid it</span></td>
    </tr>
    <tr>
        <td scope="row" data-label="Name"><a href="https://packages.trisquel.org/aramo/abrowser">Abrowser</a></td>
        <td data-label="Anti-privacy features" class="yellow-bg"><span>Makes a few requests on startup, because some spyware Firefox features are not disabled (e.g.: firefox sync)</span></td>
        <td data-label="Default search engine" class="red-bg"><span>DuckDuckGo</span></td>
        <td data-label="Code" class="green-bg"><span>MPL-2.0 / GPL-3.0</span></td>
        <td data-label="Additional features">Tracker blocking</td>
        <td data-label="Chromium based">No</td>
        <td data-label="Summary" class="yellow-bg"><span>This is like the rolling release version of GNU Icecat. Icecat does a way better job at removing Firefox spyware so you should just use Icecat</span></td>
    </tr>
    <tr>
        <td scope="row" data-label="Name"><a href="https://www.torproject.org/download/">Tor Browser</a></td>
        <td data-label="Anti-privacy features" class="yellow-bg"><span>It sends requests to torproject.org and to Mozilla when you start it, however these requests can be disabled.</span></td>
        <td data-label="Default search engine" class="red-bg"><span>DuckDuckGo</span></td>
        <td data-label="Code" class="green-bg"><span>BSD 3-clause</span></td>
        <td data-label="Additional features">Your identity is hidden thanks to the Tor network. You can change the browsing mode and the safest disables JavaScript, heavily blocks cookies, disables canvas and gives you additional privacy features</td>
        <td data-label="Chromium based">No</td>
        <td data-label="Summary" class="green-bg"><span>Recommended, just don't use DuckDuckGo</span></td>
    </tr>
    <tr>
        <td scope="row" data-label="Name"><a href="https://librewolf.net/">LibreWolf</a></td>
        <td data-label="Anti-privacy features" class="yellow-bg"><span>It makes a few requests on startup, however these can be disabled.</span></td>
        <td data-label="Default search engine" class="red-bg"><span>DuckDuckGo</span></td>
        <td data-label="Code" class="green-bg"><span>MPL-2.0</span></td>
        <td data-label="Additional features">Disables multiple privacy concerning features and has ad block (uBlock Origin)</td>
        <td data-label="Chromium based">No</td>
        <td data-label="Summary" class="green-bg"><span>Recommended, just don't use DuckDuckGo</span></td>
    </tr>
    <tr>
        <td scope="row" data-label="Name"><a href="https://www.falkon.org/">Falkon</a></td>
        <td data-label="Anti-privacy features" class="yellow-bg"><span>It updates the adblock list in the background on first startup, but nothing else.</span></td>
        <td data-label="Default search engine" class="red-bg"><span>DuckDuckGo</span></td>
        <td data-label="Code" class="green-bg"><span>GPL-3.0</span></td>
        <td data-label="Additional features">Ad block</td>
        <td data-label="Chromium based">Yes</td>
        <td data-label="Summary" class="green-bg"><span>Recommended, just don't use DuckDuckGo</span></td>
    </tr>
    <tr>
        <td scope="row" data-label="Name"><a href="https://qutebrowser.org/index.html">qutebrowser</a></td>
        <td data-label="Anti-privacy features" class="green-bg"><span>None</span></td>
        <td data-label="Default search engine" class="red-bg"><span>DuckDuckGo</span></td>
        <td data-label="Code" class="green-bg"><span>GPL-3.0</span></td>
        <td data-label="Additional features">Ad blocking (not advanced), uses Vim keybinds</td>
        <td data-label="Chromium based">Yes</td>
        <td data-label="Summary" class="green-bg"><span>Recommended, just don't use DuckDuckGo</span></td>
    </tr>
    <tr>
        <td scope="row" data-label="Name"><a href="https://www.gnu.org/software/gnuzilla/">GNU Icecat</a></td>
        <td data-label="Anti-privacy features" class="green-bg"><span>None</span></td>
        <td data-label="Default search engine" class="red-bg"><span>DuckDuckGo</span></td>
        <td data-label="Code" class="green-bg"><span>MPL-2.0 / GPL-3.0</span></td>
        <td data-label="Additional features">It has multiple privacy respecting addons (e.g.: LibreJS) and features.</td>
        <td data-label="Chromium based">No</td>
        <td data-label="Summary" class="green-bg"><span>Recommended, just don't use DuckDuckGo and make sure that you use an up-to-date build. GNU Guix has recent binaries.</span></td>
    </tr>
    <tr>
        <td scope="row" data-label="Name"><a href="https://github.com/Eloston/ungoogled-chromium">Ungoogled Chromium</a></td>
        <td data-label="Anti-privacy features" class="green-bg"><span>None</span></td>
        <td data-label="Default search engine" class="green-bg"><span>None, you have to set one yourself</span></td>
        <td data-label="Code" class="green-bg"><span>BSD 3-clause</span></td>
        <td data-label="Additional features">-</td>
        <td data-label="Chromium based">Yes</td>
        <td data-label="Summary" class="green-bg"><span>Recommended</span></td>
    </tr>
    </tbody>
</table>
<p><a href="/programs">Back to comparison</a></p>
