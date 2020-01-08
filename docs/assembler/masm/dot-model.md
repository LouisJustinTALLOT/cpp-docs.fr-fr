---
title: .MODEL
ms.date: 11/05/2019
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: 92f14a352e5c177d767232eed36a7e705fd155ce
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317628"
---
# <a name="model-32-bit-masm"></a>. MODÈLE (MASM 32 bits)

Initialise le modèle de mémoire du programme. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> **. Memory Model** *-Model* ⟦ __,__ *Language-type*⟧ ⟦ __,__ *Stack-option*⟧

### <a name="parameters"></a>Parameters

\ *de modèle de mémoire*
Paramètre obligatoire qui détermine la taille des pointeurs du code et des données.

*Language-type*\
Paramètre facultatif qui définit les conventions d’appel et de nommage pour les procédures et les symboles publics.

\ d' *option de pile*
Paramètre facultatif.

*Stack-option* n’est pas utilisé si *le modèle de mémoire* est **plat**.

La spécification de **NEARSTACK** regroupe le segment de pile en un seul segment physique (**Dgroup**), ainsi que les données. Le registre de segment de pile (**SS**) est supposé contenir la même adresse que le registre de segment de données (**DS**). **FARSTACK** ne regroupe pas la pile avec **Dgroup**; par conséquent, **SS** n’est pas égal au **DS**.

## <a name="remarks"></a>Notes

**. Le modèle** n’est pas utilisé dans [MASM pour x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

Le tableau suivant liste les valeurs possibles pour chaque paramètre lors du ciblage des plateformes 16 bits et 32 bits :

|Paramètre|Valeurs 32 bits|Valeurs 16 bits (prise en charge du développement en 16 bits antérieur)|
|---------------|--------------------|----------------------------------------------------------------|
|*modèle de mémoire*|**PLATE**|**petite**, **petite**, **compacte**, **moyenne**, **grande** **, grande,** **plate**|
|*Language-type*|**C**, **StdCall**|**C**, **BASIC**, **FORTRAN**, **PASCAL**, **SYSCALL**, **STDCALL**|
|*option de pile*|Non utilisé|**NEARSTACK**, **FARSTACK**|

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

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
