# AudioRelay flake

A nix flake to package AudioRelay

## Shell Usage

`$ export NIXPKGS_ALLOW_UNFREE=1`

`$ nix --experimental-features 'nix-command flakes' shell --impure github:JamesReynolds/audiorelay-flake -c audio-relay`

## configuration.nix

1. First, ensure that you have enabled flakes in your NixOS system

    `nix.settings.experimental-features = [ "nix-command" "flakes" ];`

2. Add the package from the remote flake like this:

    ```nix
    environment.systemPackages = with pkgs; [
        (builtins.getFlake "github:JamesReynolds/audiorelay-flake").defaultPackage.x86_64-linux
    ];
    ```

3. Run `nixos-rebuild switch` to apply the changes to your system.
