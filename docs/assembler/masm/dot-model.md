---
title: .MODEL
ms.date: 11/05/2019
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: bfc114a6e71c0eb0ae70005c2657871b6c9e9692
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398112"
---
# <a name="model-32-bit-masm"></a>.MODEL (32-bit MASM)

Initialise le modèle de mémoire du programme. (32-bit MASM only.)

## <a name="syntax"></a>Syntaxe

> **.MODEL** *memory-model* ⟦ __,__ *language-type*⟧ ⟦ __,__ *stack-option*⟧

### <a name="parameters"></a>Paramètres

*memory-model*\
Paramètre obligatoire qui détermine la taille des pointeurs du code et des données.

*language-type*\
Paramètre facultatif qui définit les conventions d’appel et de nommage pour les procédures et les symboles publics.

*stack-option*\
Paramètre facultatif.

*stack-option* is not used if *memory-model* is **FLAT**.

Specifying **NEARSTACK** groups the stack segment into a single physical segment (**DGROUP**) along with data. The stack segment register (**SS**) is assumed to hold the same address as the data segment register (**DS**). **FARSTACK** does not group the stack with **DGROUP**; thus **SS** does not equal **DS**.

## <a name="remarks"></a>Notes

**.MODEL** is not used in [MASM for x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

Le tableau suivant liste les valeurs possibles pour chaque paramètre lors du ciblage des plateformes 16 bits et 32 bits :

|Paramètre|Valeurs 32 bits|Valeurs 16 bits (prise en charge du développement en 16 bits antérieur)|
|---------------|--------------------|----------------------------------------------------------------|
|*memory-model*|**FLAT**|**TINY**, **SMALL**, **COMPACT**, **MEDIUM**, **LARGE**, **HUGE**, **FLAT**|
|*language-type*|**C**, **STDCALL**|**C**, **BASIC**, **FORTRAN**, **PASCAL**, **SYSCALL**, **STDCALL**|
|*stack-option*|Non utilisé|**NEARSTACK**, **FARSTACK**|

## <a name="code"></a>Code

Pour des exemples liés à MASM, téléchargez les exemples de compilateur dans [Exemples Visual C++ et documentation associée pour Visual Studio 2010](https://go.microsoft.com/fwlink/p/?linkid=178749).

L’exemple suivant montre l’utilisation de la directive `.MODEL`.

## <a name="example"></a>Exemple

```asm
; file simple.asm
; For x86 (32-bit), assemble with debug information:
;   ml -c -Zi simple.asm
; For x64 (64-bit), assemble with debug information:
;   ml64 -c -DX64 -Zi simple.asm
;
; In this sample, the 'X64' define excludes source not used
;  when targeting the x64 architecture

ifndef X64
.686p
.XMM
.model flat, C
endif

.data
; user data

.code
; user code

fxn PROC public
  xor eax, eax ; zero function return value
  ret
fxn ENDP

end
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)
