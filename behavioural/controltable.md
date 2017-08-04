# Control Table

The Control Table pattern is also known as a **table-driven method**.

## Intent

Control tables are a scheme that allows you to look up information in a table rather than using logic statements (``if``/``else`` and ``switch``/``case``) to determine the appropriate control flow. It allows one to simplify complex logic, and can make maintaining logic simpler and more explicit.

## Motivation


## Applicability

Consider using this when you are writing a lot of control statements (perhaps to set a variable with the appropriate value) with the same logic being reused for each case.

## Structure

Let's pretend you are writing a generic function to read from a given register of a chip that you communicate with using packets in some protocol.

You might start off writing something like:

```c
typedef enum {
  DEVICE_REGISTER_A,
  DEVICE_REGISTER_B,
  DEVICE_REGISTER_C,
  NUM_DEVICE_REGISTER
} DeviceRegister;

bool read_register(DeviceRegister reg, uint8_t *data) {
  if (reg == DEVICE_REGISTER_A) {
    return send(DEVICE_REGISTER_A_COMMAND);
  }
  if (reg == DEVICE_REGISTER_B) {
    return send(DEVICE_REGISTER_B_COMMAND);
  }
  if (reg == DEVICE_REGISTER_C) {
    return send(DEVICE_REGISTER_C_COMMAND);
  }
  // error
  return false;
}
```

If you're more ambitious, you might've written this as a ``switch``/``case`` statement.

```c
bool read_register(DeviceRegister *reg, uint8_t *data) {
  switch(reg) {
    case DEVICE_REGISTER_A:
      return send(DEVICE_REGISTER_A_COMMAND);
    case DEVICE_REGISTER_B:
      return send(DEVICE_REGISTER_B_COMMAND);
    case DEVICE_REGISTER_C:
      return send(DEVICE_REGISTER_C_COMMAND);
    default:
      // error
      return false;
  }
}
```

This can be simplified using a control table.

```c
static uint16_t s_reg_cmd[NUM_DEVICE_REGISTER] = { 
  DEVICE_REGISTER_A_COMMAND,
  DEVICE_REGISTER_B_COMMAND,
  DEVICE_REGISTER_C_COMMAND
}

bool read_register(DeviceRegister *reg, uint8_t *data) {
  if (reg > NUM_DEVICE_REGISTER) {
    // error
    return false;
  }

  return send(s_reg_cmd[reg]);
}
```
