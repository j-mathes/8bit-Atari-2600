	processor 6502
        
        include "vcs.h"
        include "macro.h"
        
        seg Code
        org $f000	; start code at $f000
        
Start	sei		; disable interrupts
	cld		; disable BCD math mode
        ldx #$ff	; init stack pointer to $ff
        txs		; transfer X register to S register
        
        		; reset memory to known state
        lda #0		; set A register to zero
        ldx #$ff	; set X ro #$ff
ZeroZP	sta $0,X	; store A register at address ($0 + X)
	dex		; decrement X by 1
        bne ZeroZP	; branch until X is zero
        
        lda #$30	; load value into A ($30 is deep red)
        sta COLUBK	; store A into the background color register
        
        jmp Start
        
        org $fffc
        .word Start	; reset vector at $fffc
        .word Start	; interrupt vector at $fffe (unused in VCS)
