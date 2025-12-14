# ERD (High-level)

Entity minimal MVP:
- tenants (opsional, kalau multi bisnis)
- outlets
- users (role, outlet scope)
- menu_categories
- menu_items
- modifier_groups
- modifier_options
- item_modifier_groups (relasi)
- orders
- order_items
- order_item_modifiers
- payments
- shifts
- cash_movements
- order_events

Catatan:
- Money integer Rupiah
- Timestamp UTC
- UUID untuk primary key
