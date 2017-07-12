#!/usr/bin/env python3

import requests

from operator import itemgetter


if __name__ == "__main__":
	r = requests.get("https://raw.githubusercontent.com/jshttp/mime-db/master/db.json")

	mime_types = []
	for mime_type, attrs in r.json().items():
		mime_types.append((mime_type, attrs.get("extensions", [])))

	last_group = None
	for mime_type, extensions in sorted(mime_types, key=itemgetter(0)):
		current_group = mime_type.split("/")[0]
		if last_group and current_group != last_group:
			print()

		print("{:<64} {}".format(mime_type, " ".join(extensions)))

		last_group = current_group
