#
# Please note not all available settings / options are set here.
# For a full list, see the wiki
#


# See https://wiki.hyprland.org/Configuring/Monitors/
# notebook monitor
monitor=eDP-1, 1920x1080, 0x0, 1
# office main monitor / secondary monitor
monitor=HDMI-A-1, 1920x1080@75, 1920x0, 1
monitor=DP-1, 1920x1080, 3840x0, 1
# home 4k monitor / 144hz monitor
# monitor=HDMI-A-1, 3840x2160, 1920x0, 1.5
# monitor=HDMI-A-1,1920x1080@144,auto,1



# See https://wiki.hyprland.org/Configuring/Keywords/ for more

# Execute your favorite apps at launch
exec-once = waybar & swaybg -i ~/.config/wallpaper.jpg
exec-once = /usr/bin/dunst
# Source a file (multi-file configs)
# source = ~/.config/hypr/myColors.conf

# Some default env vars.
env = XCURSOR_SIZE,24

# For all categories, see https://wiki.hyprland.org/Configuring/Variables/
input {
    kb_layout = us
    kb_variant = altgr-intl
    kb_model =
    kb_options =
    kb_rules =

    follow_mouse = 2

    touchpad {
        natural_scroll = no
    }

    sensitivity = 0 # -1.0 - 1.0, 0 means no modification.
    numlock_by_default = true
}

general {
    # See https://wiki.hyprland.org/Configuring/Variables/ for more

    gaps_in = 3
    gaps_out = 8
    border_size = 4
    col.active_border = 0xfff5e0dc
    col.inactive_border = 0xaa585b70

    layout = dwindle
}

decoration {
    # See https://wiki.hyprland.org/Configuring/Variables/ for more

    rounding = 8
    
    blur {
        enabled = true
        size = 16
        passes = 2
        noise = 0.2
        new_optimizations = true
    }

    layerrule = blur, waybar
    layerrule = blur, bemenu

    # drop_shadow = yes
    # shadow_range = 4
    # shadow_render_power = 3
    # col.shadow = rgba(1a1a1aee)
}

animations {
    enabled = yes

    # Some default animations, see https://wiki.hyprland.org/Configuring/Animations/ for more
 # Some default animations, see https://wiki.hyprland.org/Configuring/Animations/ for more
    bezier = myBezier, 0.10, 0.9, 0.1, 1.0

    animation = windows, 1, 5, myBezier, slide
    animation = windowsOut, 1, 5, myBezier, slide
    animation = border, 1, 10, default
    animation = fade, 1, 7, default
    animation = workspaces, 1, 6, default
}

dwindle {
    # See https://wiki.hyprland.org/Configuring/Dwindle-Layout/ for more
    pseudotile = yes # master switch for pseudotiling. Enabling is bound to mainMod + P in the keybinds section below
    preserve_split = yes # you probably want this
}

master {
    # See https://wiki.hyprland.org/Configuring/Master-Layout/ for more
    # new_is_master = true
}

gestures {
    # See https://wiki.hyprland.org/Configuring/Variables/ for more
    workspace_swipe = off
}

misc {
    disable_hyprland_logo = true
}

# Example per-device config
# See https://wiki.hyprland.org/Configuring/Keywords/#executing for more
# device:epic-mouse-v1 {
#   sensitivity = -0.5
# }

# Example windowrule v1
# windowrule = float, ^(kitty)$
# Example windowrule v2
# windowrulev2 = float,class:^(kitty)$,title:^(kitty)$
# See https://wiki.hyprland.org/Configuring/Window-Rules/ for more


# See https://wiki.hyprland.org/Configuring/Keywords/ for more
$mainMod = SUPER
$left = H
$right = L
$up = K
$down = J
$menu = bemenu-run 


# Example binds, see https://wiki.hyprland.org/Configuring/Binds/ for more
bind = $mainMod, Return, exec, wezterm
bind = $mainMod SHIFT, Return, exec, alacritty
bind = $mainMod, W, killactive, 
bind = $mainMod, Escape, exit, 
bind = $mainMod SHIFT, P, exec, grim -g "$(slurp)" ~/Pictures/$(date +'%s_grim.png')
bind = $mainMod, P, exec, grim -g "$(slurp)" - | wl-copy
bind = $mainMod SHIFT, O, exec, grim ~/Pictures/$(date +'%s_grim.png')
bind = $mainMod, O, exec, grim - | wl-copy
# bind = $mainMod, Space, exec, wofi --show drun
bind = $mainMod, Space, exec, bemenu-run --hp 8 -B 1 --bdr "##1e1e2e" --fn "Inter Font 16px" --fb "##1e1e2e" --ff "##cdd6f4" --nb "##1e1e2e" --nf "##cdd6f4" --tb "##1e1e2e" --hb "##1e1e2e" --tf "##f38ba8" --hf "##f9e2af" --nf "##cdd6f4" --af "##cdd6f4" --ab "##1e1e2e"
bind = $mainMod, E, togglefloating, 
bind = $mainMod, Q, pseudo, # dwindle
bind = $mainMod, R, togglesplit, # dwindle
bind = $mainMod, G, fullscreen, 0

# Move focus with mainMod + arrow keys
bind = $mainMod, $left, movefocus, l
bind = $mainMod, $right, movefocus, r
bind = $mainMod, $up, movefocus, u
bind = $mainMod, $down, movefocus, d

bind = $mainMod SHIFT, $left, movewindow, l
bind = $mainMod SHIFT, $right, movewindow, r
bind = $mainMod SHIFT, $up, movewindow, u
bind = $mainMod SHIFT, $down, movewindow, d

bind = $mainMod CTRL, $left, swapwindow, l
bind = $mainMod CTRL, $right, swapwindow, r
bind = $mainMod CTRL, $up, swapwindow, u
bind = $mainMod CTRL, $down, swapwindow, d

bind = $mainMod ALT, $left, movecurrentworkspacetomonitor, l
bind = $mainMod ALT, $right, movecurrentworkspacetomonitor, r
bind = $mainMod ALT, $up, movecurrentworkspacetomonitor, u
bind = $mainMod ALT, $down, movecurrentworkspacetomonitor, d

# Switch workspaces with mainMod + [0-9]
bind = $mainMod, A, workspace, 1
bind = $mainMod, S, workspace, 2
bind = $mainMod, D, workspace, 3
bind = $mainMod, F, workspace, 4
bind = $mainMod, Z, workspace, 5
bind = $mainMod, X, workspace, 6
bind = $mainMod, C, workspace, 7
bind = $mainMod, V, workspace, 8
bind = $mainMod, 1, workspace, 9
bind = $mainMod, 2, workspace, 10
bind = $mainMod, 3, workspace, 11
bind = $mainMod, 4, workspace, 12

bind = $mainMod SHIFT, A, movetoworkspace, 1
bind = $mainMod SHIFT, S, movetoworkspace, 2
bind = $mainMod SHIFT, D, movetoworkspace, 3
bind = $mainMod SHIFT, F, movetoworkspace, 4
bind = $mainMod SHIFT, Z, movetoworkspace, 5
bind = $mainMod SHIFT, X, movetoworkspace, 6
bind = $mainMod SHIFT, C, movetoworkspace, 7
bind = $mainMod SHIFT, V, movetoworkspace, 8
bind = $mainMod SHIFT, 1, movetoworkspace, 9
bind = $mainMod SHIFT, 2, movetoworkspace, 10
bind = $mainMod SHIFT, 3, movetoworkspace, 11
bind = $mainMod SHIFT, 4, movetoworkspace, 12

# Scroll through existing workspaces with mainMod + scroll
bind = $mainMod, mouse_down, workspace, e+1
bind = $mainMod, mouse_up, workspace, e-1

# Move/resize windows with mainMod + LMB/RMB and dragging
bindm = $mainMod, mouse:272, movewindow
bindm = $mainMod, mouse:273, resizewindow

bind = ,XF86AudioRaiseVolume, exec, pactl set-sink-volume @DEFAULT_SINK@ +5%
bind = ,XF86AudioLowerVolume, exec, pactl set-sink-volume @DEFAULT_SINK@ -5%
bind = ,XF86AudioMute, exec, pactl set-sink-mute @DEFAULT_SINK@ toggle
bind = ,XF86AudioMicMute, exec, pactl set-source-mute @DEFAULT_SOURCE@ toggle
bind = ,XF86MonBrightnessDown, exec, brightnessctl set 5%-
bind = ,XF86MonBrightnessUp, exec, brightnessctl set 5%+
bind = ,XF86AudioPlay, exec, playerctl play-pause
bind = ,XF86AudioNext, exec, playerctl next
bind = ,XF86AudioPrev, exec, playerctl previous
