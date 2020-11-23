# bsc-v2
Enhanced version of bsc-v2 providing custom metadata columns for caja, nautilus file managers

The file managers Caja (for MATE) Nemo (Cinammon) and GNOME Files (formerly Nautulius) all have a related code
base for which bsc-v2.py was written by Giacomo Bordiga to provide custom columns with extra metadata.

The 3 subsequent versions Nautilus columns (https://github.com/atareao/nautilus-columns)
caja columns (https://gist.github.com/infirit/497d589c4dcf44ffe920) nemo-media-columns 
(https://github.com/linuxmint/nemo-extensions/tree/master/nemo-media-columns) all suffered from the same
fault, not carrying the list view custom columns to the icon view, and not providing consistent title
metadata for all filetypes.

This repository attempts to fix that for caja-columns and nautilus-columns. nemo-media-columns was changed too
much to be updated.

It populates 'title' from
  Xmp.dc.title for images
  metadata.get_title for video 
  info.title for PDFs
  audio['title'] for audio
  
It populates 'description' from
  Exif.Image.ImageDescription for images
  metadata.get_description for video  
  info.subject for PDFs
  blank for audio

It also renames the 'artist' column 'creator' as more appropriate for images/pdfs

To use
  copy caja-columns.py to /usr/share/caja-python/extensions
  copy nautilus-columns.py to /usr/share/nautilus-python/extensions

