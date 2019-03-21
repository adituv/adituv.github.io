# ROM Map

ROM map for Golden Sun (USA, Europe).

## 0x08000000 - Header

Cartridge header; see GBATek for details.  Entry point: [`arm_start@080003c0`](#0x080003c0---arm_start)

## 0x080000c0 - Thunks

TODO: thunk table

## 0x080003c0 - arm\_start

Prototype: `void arm_start(void)`

The game's entrypoint, and where control begins after a hard reset.

### Pseudocode

```C
__ARM
void arm_start(void) {
    while (true) {
        SET_PROCESSOR_MODE(PSR_M_IRQ);
        SET_STACK_POINTER(STACKBASE_IRQ);
        SET_PROCESSOR_MODE(PSR_M_SYS);
        SET_STACK_POINTER(STACKBASE_SYS);

        IRQ_HANDLER = &userIrqHandler_src;
        thumb_start();
    }
}
```

Referenced symbols:
* [`userIrqHandler_src@08000770`](#0x08000770---userirqhandler_src)
* [`thumb_start@08002e00`](#0x08002e00---thumb_start)

## 0x08000770 - userIrqHandler\_src

... todo

## 0x08002e00 - thumb\_start

... todo
