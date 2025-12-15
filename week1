                    ┌─────────────────────────┐
                    │     Host Machine         │
                    │   (Windows / macOS)      │
                    │                          │
                    │  VirtualBox Host-Only    │
                    │      Network             │
                    │  192.168.56.0/24         │
                    └───────────┬─────────────┘
                                │
          ┌─────────────────────┴─────────────────────┐
          │                                           │
┌──────────────────────┐                 ┌──────────────────────┐
│   Ubuntu Server VM   │                 │ Ubuntu Workstation VM│
│                      │                 │                      │
│  IP: 192.168.56.10   │◄──────────────► │  IP: 192.168.56.20   │
│  Role: Server        │                 │  Role: Client        │
│                      │                 │                      │
│  Adapter 1: NAT      │                 │  Adapter 1: NAT      │
│  Adapter 2: HostOnly │                 │  Adapter 2: HostOnly │
└──────────────────────┘                 └──────────────────────┘
