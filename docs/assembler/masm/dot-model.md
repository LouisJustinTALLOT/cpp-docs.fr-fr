---
description: En savoir plus sur :. MODÈLE (MASM 32 bits)
title: .MODEL
ms.date: 11/05/2019
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: a4324b89f1194227edd7f1d5b7bd70560eca16be
ms.sourcegitcommit: 6183207b11575d7b44ebd7c18918e916a0d8c63d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97951418"
---
# <a name="model-32-bit-masm"></a>. MODÈLE (MASM 32 bits)

Initialise le modèle de mémoire du programme. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntax

> **. Memory Model** *-Model* ⟦__,__ *Language-type*⟧ ⟦__,__ *Stack-option*⟧

### <a name="parameters"></a>Paramètres

*modèle de mémoire*\
Paramètre obligatoire qui détermine la taille des pointeurs du code et des données.

*Language-type*\
Paramètre facultatif qui définit les conventions d’appel et de nommage pour les procédures et les symboles publics.

*option de pile*\
Paramètre facultatif.

*Stack-option* n’est pas utilisé si *le modèle de mémoire* est **plat**.

La spécification de **NEARSTACK** regroupe le segment de pile en un seul segment physique (**Dgroup**), ainsi que les données. Le registre de segment de pile (**SS**) est supposé contenir la même adresse que le registre de segment de données (**DS**). **FARSTACK** ne regroupe pas la pile avec **Dgroup**; par conséquent, **SS** n’est pas égal au **DS**.

## <a name="remarks"></a>Remarques

**. Le modèle** n’est pas utilisé dans [MASM pour x64 (ml64.exe)](masm-for-x64-ml64-exe.md).

Le tableau suivant liste les valeurs possibles pour chaque paramètre lors du ciblage des plateformes 16 bits et 32 bits :

|Paramètre|Valeurs 32 bits|Valeurs 16 bits (prise en charge du développement en 16 bits antérieur)|
|---------------|--------------------|----------------------------------------------------------------|
|*modèle de mémoire*|**PLATE**|**petite**, **petite**, **compacte**, **moyenne**, **grande** **, grande,** **plate**|
|*Language-type*|**C**, **StdCall**|**C**, **Basic**, **Fortran**, **Pascal**, **syscall**, **StdCall**|
|*option de pile*|Non utilisé|**NEARSTACK**, **FARSTACK**|

## <a name="code"></a>Code

Pour des exemples liés à MASM, téléchargez les exemples de compilateur dans [Exemples Visual C++ et documentation associée pour Visual Studio 2010](https://github.com/Microsoft/vcsamples).

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

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
