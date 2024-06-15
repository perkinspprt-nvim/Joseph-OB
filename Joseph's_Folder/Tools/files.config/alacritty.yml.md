
```YAML

# alacritty.yml   
   

font:
size: 10   
# Normal (roman) font face   
normal:
# Font family
#
# Default:
#   - (macOS) Menlo
#   - (Linux/BSD) monospace
#   - (Windows) Consolas
family: JetBrainsMono Nerd Font   
schemes:
hyper\_theme: &hyper
primary:
background: '0x000000'
foreground: '0xffffff'
cursor:
text: '0xF81CE5'
cursor: '0xffffff'   
# Bright colors   
bright:
black:   '0x808080'
red:     '0xfe0100'
green:   '0x33ff00'
yellow:  '0xfeff00'
blue:    '0x0066ff'
magenta: '0xcc00ff'
cyan:    '0x00ffff'
white:   '0xFFFFFF'
deep\_ocean\_theme: &ayu
primary:
background: '0x0A0E14'
foreground: '0xB3B1AD'   
moonfly\_theme: &moonfly
primary:
background: '#080808'
foreground: '0xdfbf8e'   
gruvbox\_theme: &gruvbox
primary:
# hard contrast: background = '0x1d2021'
background: '#282828'
# soft contrast: background = '0x32302f'
foreground: '#ebdbb2'   
kanagawa\_theme: &kanagawa
primary:
background: '#1f1f28'
foreground: '#dcd7ba'   
tokyo-night: &tokyo-night
primary:
background: '#1A1B26'
foreground: '#a9b1d6'   
rose-pine\_theme: &rose-pine
primary:
background: '#191724'
foreground: '#e0def4'
normal:
black:   '#6e6a86'
red:     '#eb6f92'
green:   '#9ccfd8'
yellow:  '#f6c177'
blue:    '#54aacc'
magenta: '#c4a7e7'
cyan:    '#ebbcba'
white:   '#e0def4'   
colors: gruvbox
cursor:
style:
shape: Beam
blinking: Always
blink\_interval: 700
unfocused\_hollow: true
thickness: 0.10
window:
decorations: none
padding:
x: 8
y: 5
shell:
program: /usr/bin/bash   
   
