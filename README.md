# OpenCode Skill OpenSCAD

## Tests

### Test 1

Prompt: Could you create an OpenSCAD file for a cube of size 100 mm?

Result:

```
cube_size = 100;

$fn = 64;

cube(cube_size, center = true);
```

[OpenSCAD Playground](https://ochafik.com/openscad2/#H4sIAAAAAAAAA3WQy27bMBBFf0WYdJECSpq6hd0oMAqnRXcBJG2yYIyAljgyaYpUyaFt2dW/F5SQBFkE3Ny5PPM8Q8cdbz1kZ+AVyb3IOW0hgy+d5n3jbDD1ta94DSl4G1wlPGTsDN2HVGUNCUOQQRU24tnLk0iWydebm7sn82Q+oUmWyfz7GETg8pVKk0oYEi5ZJuSC+HwHwzoFFJyCG7uC5qf+KhhpDaxTEMfOOvpjXctp9hsy8PsG3tvfRps0DCnspTjELTXvbaCoWlsLyKANmmRMrCVZB1lsPuHiNaqCJ9vKU3SQay+GuKiOOFzgbb2YVfFAW3tYHeOsU5a2jX/jOydeZtjo4Lbcxwv++1t2s43F65Vt1JoWD88W+dEKLNQaC5wrxnsscHf1U7GHA+/jsxeKKUaL8W+uGOZYRk23ipVyYna/FMOSfmD+eK8YFliMXPG4wtw2WEY9Vi5oMapddCaylBMTI37EnPcwDP8BhKBrFioCAAA=)

### Test 2

Prompt: Could you create an OpenSCAD file for a panel of thickness 5 mm, height 200 mm, and width
100 mm? There should also be two holes of 10 mm diameter, horizontally centred, and evenly spaced
vertically.

Result:

```
$fn = 64;

panel_thickness = 5;
panel_height    = 200;
panel_width     = 100;

hole_diameter = 10;
hole_radius   = hole_diameter / 2;

module panel() {
    difference() {
        cube([panel_width, panel_height, panel_thickness]);

        for (y = [panel_height / 3, 2 * panel_height / 3]) {
            translate([panel_width / 2, y, -1])
                cylinder(h = panel_thickness + 2, r = hole_radius);
        }
    }
}

panel();
```

[OpenSCAD Playground](https://ochafik.com/openscad2/#H4sIAAAAAAAAA3VS227bMAz9FYHbQ7o5vaRb27kwBi9Dgb6sbTrAD45RKDZly5GlQJfEbuZ/H+QuaVNgAgyIhzzkoXy2sKKaNgbCLdDc8jXeU1tBCCcrQbtSKyeLY5PTAgJgSK3TaCBMQdDnbuwkVxKyAIxyOh8SW1j9l58raVFaCOEjkyQiF1+u53IuV1SieLIVz5cSjSER+Xq9QyvkZWUJISQik9PTPb7hha08TCJyNuBzWSmBTwWnDVrUA379D9S04M4MxYdFJ2QyUBtVOIFk6D06Itu59K0LzhhqlDm+Yv7kboGj9I2QgLxVu4v2G2VHw5AdnSlNRh2JSHqw4wk5D8iEfCLv0exguD9WU2kEtYcq/DYB6QIyPsuODgmD6k5wWaAeVSR6r5B89lT/aG/ey6vekfuXaz+X/f6XjXwB9FkA2K6UtjdKN9ROfkIIZl3CIXw+wFZAH8Ca48b7TajSQMioMBiAoJ1y1sONKhBCaJyw3LtO5e61DAtulYbQaocvnXAf5c5Y1fBnjwzlvfecEHRlsJjuk7/pwjs1G5K+F3xg34rLSQ4BmEpt4tY7+aWl4BJ/uWaBeiehD2ClcbfCQjhdUeMN/2fxeDM+r6Px99axB3uZxPaCPbTOXlGc3dFWlXVap7Q7juvs9tHfkx8+rjN1O7ur03aznNK2zmhLuxlfTlWZxOy+zuq0zmhnQnulWBLX6YwnsSrZcsimvloxVbKHJLaXPvKfvWKzJFbMM+tUMT8niWm7nELf/wXS3Vkr8wMAAA==)

Prompt: Could you make that three holes instead?

Result:

```
$fn = 64;

panel_thickness = 5;
panel_height    = 200;
panel_width     = 100;

hole_diameter = 10;
hole_radius   = hole_diameter / 2;

module panel() {
    difference() {
        cube([panel_width, panel_height, panel_thickness]);

        for (y = [panel_height / 4, 2 * panel_height / 4, 3 * panel_height / 4]) {
            translate([panel_width / 2, y, -1])
                cylinder(h = panel_thickness + 2, r = hole_radius);
        }
    }
}

panel();
```

[OpenSCAD Playground](https://ochafik.com/openscad2/#H4sIAAAAAAAAA3WTa2+bMBSG/4p1tg/pRnpJu7ajQhPLVKlf1iadxAeCKgdssGNs5EsDzfjvk8mSNrtYQuI8Pu/hvOZ4Aw3WuDYQbgDnlj2TB2wrCOGkEbgrtXKyODY5LiAASrB1mhgIUxD4pRs7yZSELACjnM6HjQ00/9XnSloiLYTwnkoUocuLm4VcyAZLIp5sxfKVJMagCH262dGKsLKyCCEUocnp6Z6vWWErj1GEzga+kJUS5KlguCaW6IHf/IYaF8yZIfkw6QRNBmmtCicIGmqPjtBmIX3pglFKNJE5eWV+5W5JRumbRgL0tttdtHeUHQ0f2cmp0mjUoQilBx5P0EWAJugD+pue/4NmBy35ZTWWRmB72Jv3GKAuQOOz7OhQMHjpBJMF0aMKRX/2jT56qT/KN6fovezE/fa1X8h+/yNHW7PQZwGQtlHa3ipdYzv5BiGY5xIO8fmArYA+gGdG1n4OhSoNhBQLQwIQuFPOelyrgkAItROW+WlUuXtNIwWzSkNotSPbSmQf5c5YVbMXT4b03s+iELgxpJjuN3/gpZ/gbNj0teAd/VxcTXIIwFRqHbd+wrclBZPku6uXRO9a6ANoNNlZWAqnK2z8Rfi5fLwdn/No/KV1dGavkthe0lnr7DUm83vcqpKndIW745hnd4885Wny1cc8U3fze56269UUtzzDLe7mbDVVZRLTB57xlGe4U9Ree8LTOUtiXyuJ6WzIbhVVJZ0lsb3yWv/YazpPYkW9kqeK8hR3SYzb1RT6/heAn0JECwQAAA==)

### Test 3

Prompt: Could you create an OpenSCAD model for a cylinder of length 200 mm and diamter 30 mm? It should also have knurling on half the length.

(Took some further prompting to get the knurling right).

```
$fn = 64;

CYL_LENGTH = 200;
CYL_DIAM   = 30;
CYL_R      = CYL_DIAM / 2;

KNURL_ANGLE = 30;
KNURL_COUNT = 36;
KNURL_DEPTH = 0.4;
KNURL_WIDTH = 0.3;

module knurl_section(h, r) {
    twist = h * tan(KNURL_ANGLE) / r * 180 / PI;

    module grooves(twist_dir) {
        linear_extrude(height = h, twist = twist_dir * twist, slices = h * 2)
            for (i = [0:KNURL_COUNT - 1])
                rotate([0, 0, i * 360 / KNURL_COUNT])
                    translate([r - KNURL_DEPTH, 0])
                        square([KNURL_DEPTH, KNURL_WIDTH]);
    }

    difference() {
        cylinder(h = h, r = r);
        grooves(1);
        grooves(-1);
    }
}

translate([0, 0, CYL_LENGTH / 2])
    cylinder(h = CYL_LENGTH / 2, r = CYL_R);

knurl_section(CYL_LENGTH / 2, CYL_R);
```

