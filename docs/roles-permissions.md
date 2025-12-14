# Roles & Permissions

## Roles
- OWNER (atau ADMIN)
- CASHIER
- KITCHEN

## Permission Matrix (MVP)
| Action | OWNER | CASHIER | KITCHEN |
|------|:-----:|:------:|:------:|
| Manage menu (items/modifiers) | Yes | No | No |
| Manage users/roles | Yes | No | No |
| View reports | Yes | Limited (opsional) | No |
| Open/close shift | Yes | Yes | No |
| Cash in/out | Yes | Yes | No |
| Create order | Yes | Yes | No |
| Send to kitchen | Yes | Yes | No |
| Update kitchen status (COOKING/READY) | Yes | No | Yes |
| Take payment | Yes | Yes | No |
| Void order | Yes | Conditional* | No |
| Refund (jika ada) | Yes | Conditional* | No |

Catatan:
- *Conditional = CASHIER boleh jika ada policy (mis. max nominal) atau butuh PIN/approval OWNER (phase berikutnya).
- Semua perubahan status penting dicatat di `order_events` (audit).
