# DBus Notifier for Node.js applications

This library provides you with a minimal but robust way to send and handle notifications using DBus.

## Usage

Take this as an example:

```js
const Notifier = require('dbus-notifier');

Notifier.new().then(async (notifier) => {
	let thisNotificationID = await notifier.notify({
			appName: "yourAppName",
			replacesId: 0, // If you have a cached notification ID to place, put it here
			icon: "update-low", // 
			summary: "Summary text",
			body: "<b>Body text with HTML parsing</b>",
			actions: [
				{
					name: "Action 1",
					key: "action-1"
				},
				{
					name: "Action 2",
					key: "action-2"
				}
			],
			hints: {
				"urgency": new Variant("y", 1),
				"category": new Variant("s", "device"),
				"desktop-entry": new Variant("s", "yourAppDesktopEntry"),
				"x-kde-origin-name": new Variant("s", "Your origin name, if any"),
				"x-kde-display-appname": new Variant("s", "Your application")
			},
			timeout: 1000 * 5
		});
		
		notifier.on("action-invoked", signal => {
			// Signal can be a string containing action-1 or action-2 in this example
			// You would need to handle it here.
		});
});
```

For extended usage please refer to Freedesktop's documentation or the project's source code.

## License

`dbus-notifier` is licensed under Mozilla Public License, version 2.0.

```
This Source Code Form is subject to the terms of the Mozilla Public
License, v. 2.0. If a copy of the MPL was not distributed with this
file, You can obtain one at http://mozilla.org/MPL/2.0/.
```

## Third party licenses

This project uses `TypedEventEmitter` by Cynthia K. Rey, which is licensed under the following license.

```
Copyright (c) 2021 Cynthia K. Rey, All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this
   list of conditions and the following disclaimer.
2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the
   documentation and/or other materials provided with the distribution.
3. Neither the name of the copyright holder nor the names of its contributors
   may be used to endorse or promote products derived from this software without
   specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

This project uses `dbus-next` by Andrey Sidorov and Tony Crisci, which is licensed under the MIT license.

```
This software is released under the MIT license:

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```
