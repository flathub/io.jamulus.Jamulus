
# Jamulus

Jamulus is a software that enables musicians to perform real-time jam sessions over the internet.

This packages [jamulus](https://github.com/jamulussoftware/jamulus) as a flatpak and publishes it on [Flathub](https://flathub.org/).

## Configuration

To use this package, you need to have [pipewire](https://pipewire.org/) set up in your system, along with the current JACK plugin.

In Fedora 34, that will be the default audio handler. On previous versions, you can do that with:
```
sudo dnf install --allowerasing pipewire-jack
```
(more info at https://fedoraproject.org/wiki/Changes/DefaultPipeWire#How_To_Test)


You can, then, install the app with:
```
flatpak install flathub io.jamulus.Jamulus
```

## Usage

The app can be launched from the Desktop Icon or with the command
```
flatpak run io.jamulus.Jamulus
```


When you launch the app, it should automatically connect to the `pipewire-jack` server. If that is not the case, you can force that by adding `pw-jack` to the beginning of the launch command.
For example, you would use:
```
pw-jack flatpak run io.jamulus.Jamulus
```
and, for accessing a tool like QJackCtl connected to the proper server:
```
pw-jack qjackctl
```

## Development

To build this package locally you need to:

1. Install flatpak dependencies:

   In Fedora:
   ```
   sudo dnf install flatpak-builder
   ```

2. Install flatpak runtime and Sdk:
   ```
   flatpak install flathub org.kde.Platform//5.15 org.kde.Sdk//5.15
   ```

3. Build the application:
   ```
   flatpak-builder build-dir io.jamulus.Jamulus.yaml
   ```
   or, to build and test:
   ```
   flatpak-builder --user --install build-dir io.jamulus.Jamulus.yaml --force-clean
   ```
