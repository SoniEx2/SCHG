# SCHG/sonic-1/enigma-credits

This guide is for those of you who need to fit more credits in a single "credits title card" screen.

## Download the required files

First, you'll need to download [EniCredProg.asm](EniCredProg.asm). This guide assumes it is located in your project's root directory.
It also assumes you're using Hivebrain's ASM68k disassembly.

You'll also need to download everything in [credeni/](credeni/).

## Reconfigure the credits object

In `sonic1.asm`, go to `Cred_ClrPallet:`, then find:

```
		move.b	#$8A,($FFFFD080).w ; load credits object
```

and replace it with:

```
		jsr	Credits_MapLoad	; We'll include this routine in the next step
```

## Including the files

Now we need to include the files. Add this before the `; end of 'ROM'`:

```
		include  EniCredProg.asm	; here we include the "Credits_MapLoad" subroutine
		even
EniCred_0:	incbin	credeni\cred0.bin	; Credits #0 mappings
		even
EniCred_1:	incbin	credeni\cred1.bin	; Credits #1 mappings
		even
EniCred_2:	incbin	credeni\cred2.bin	; Credits #2 mappings
		even
EniCred_3:	incbin	credeni\cred3.bin	; Credits #3 mappings
		even
EniCred_4:	incbin	credeni\cred4.bin	; Credits #4 mappings
		even
EniCred_5:	incbin	credeni\cred5.bin	; Credits #5 mappings
		even
EniCred_6:	incbin	credeni\cred6.bin	; Credits #6 mappings
		even
EniCred_7:	incbin	credeni\cred7.bin	; Credits #7 mappings
		even
EniCred_8:	incbin	credeni\cred8.bin	; Credits #8 mappings
		even
EniCred_9:	incbin	credeni\cred9.bin	; Credits #9 mappings
		even
```

Save and build. You should now have working enigma credits. Please note, though, that they're empty. I had issues getting PlaneED to work properly.

## PlaneED Project

The PlaneED project files are available in [planeed/](planeed/). I assume you know how to use them.

Note: I recommend using Sonic 2's credits title card font. It's much easier than using the standard Sonic 1 one.
