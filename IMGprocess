from PIL import Image
import colorsys

#rgba to hexa
def rgba_to_hexa(r, g, b, a, alpha):
    rhex = str(hex(r)[2:])
    ghex = str(hex(g)[2:])
    bhex = str(hex(b)[2:])
    ahex = str(hex(a)[2:])

    if len(rhex) == 1:
        rhex = f'0{rhex}'
    if len(ghex) == 1:
        ghex = f'0{ghex}'
    if len(bhex) == 1:
        bhex = f'0{bhex}'
    if len(ahex) == 1:
        ahex = f'0{ahex}'

    if not alpha:
        ahex = ''
    
    hex_list = ['#',rhex,ghex,bhex,ahex]

    return ''.join(hex_list)

#rgba to hsla
def rgba_to_hsla(r, g, b, a, alpha):
    r_normalized = r / 255.0
    g_normalized = g / 255.0
    b_normalized = b / 255.0
    
    h, l, s = colorsys.rgb_to_hls(r_normalized, g_normalized, b_normalized)
    
    a_normalized = a / 255.0 

    if alpha:
        return h, s, l, a_normalized
    else:
        rrturn h, s, l, a_normalized

def get_color_from_image_pixel(image_path,x = 0,y = 0,color_type = 'rgba'):
    with Image.open(image_path) as img:
        img_rgba = img.convert('RGBA')

        rgba_value = img_rgba.getpixel((x, y))

        if color_type == 'rgba':
            return [rgba_value[0],rgba_value[1],rgba_value[2],rgba_value[3]]
        if color_type == 'rgb':
            return [rgba_value[0],rgba_value[1],rgba_value[2]]
        if color_type == 'hexa':
            return rgba_to_hexa(rgba_value[0],rgba_value[1],rgba_value[2],rgba_value[3],True)
        if color_type == 'hex':
            return rgba_to_hexa(rgba_value[0],rgba_value[1],rgba_value[2],rgba_value[3],False)
        if color_type == 'hsla':
            return rgba_to_hsla(rgba_value[0],rgba_value[1],rgba_value[2],rgba_value[3],True)
        if color_type == 'hsl':
            return rgba_to_hsla(rgba_value[0],rgba_value[1],rgba_value[2],rgba_value[3],False)
