# Simple bash script to change wallpaper and colorschemes on dwm and st using dmenu and pywal

# dependencies: 
pywal, colorthief(optional), haishoku(optional), colorz(optional), xrdb
dwm with xrdb patch(to change dwm colorscheme), st with xresources patch, dmenu
notify-send, xsetroot.

# how to configure xrdb
dwm.c with xrdb patch
replace 

`

    void
    loadxrdb()
    {
      Display *display;
      char * resm;
      XrmDatabase xrdb;
      char *type;
      XrmValue value;
    
      display = XOpenDisplay(NULL);
    
      if (display != NULL) {
        resm = XResourceManagerString(display);
    
        if (resm != NULL) {
          xrdb = XrmGetStringDatabase(resm);
    
          if (xrdb != NULL) {
            XRDB_LOAD_COLOR("dwm.normbordercolor", normbordercolor);
            XRDB_LOAD_COLOR("dwm.normbgcolor", normbgcolor);
            XRDB_LOAD_COLOR("dwm.normfgcolor", normfgcolor);
            XRDB_LOAD_COLOR("dwm.selbordercolor", selbordercolor);
            XRDB_LOAD_COLOR("dwm.selbgcolor", selbgcolor);
            XRDB_LOAD_COLOR("dwm.selfgcolor", selfgcolor);
          }
        }
      }
    
      XCloseDisplay(display);
    }

` 

with

`

    void
    loadxrdb()
    {
      Display *display;
      char * resm;
      XrmDatabase xrdb;
      char *type;
      XrmValue value;
    
      display = XOpenDisplay(NULL);
    
      if (display != NULL) {
        resm = XResourceManagerString(display);
    
        if (resm != NULL) {
          xrdb = XrmGetStringDatabase(resm);
    
          if (xrdb != NULL) {
            XRDB_LOAD_COLOR("color8", normbordercolor);
            XRDB_LOAD_COLOR("background", normbgcolor);
            XRDB_LOAD_COLOR("foreground", normfgcolor);
            XRDB_LOAD_COLOR("foreground", selbordercolor);
            XRDB_LOAD_COLOR("color2", selbgcolor);
            XRDB_LOAD_COLOR("foreground", selfgcolor);
          }
        }
      }
      XCloseDisplay(display);
    }
`
