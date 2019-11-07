---
title: .MODEL
ms.date: 11/05/2019
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: b341cfaec35c08f5ac16447890c85570e9c9c0df
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703581"
---
# <a name="model-32-bit-masm"></a>. MODÈLE (MASM 32 bits)

Initialise le modèle de mémoire du programme. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> .MODEL memorymodel [[, langtype]] [[, stackoption]]

### <a name="parameters"></a>Paramètres

*memorymodel*<br/>
Paramètre obligatoire qui détermine la taille des pointeurs du code et des données.

*langtype*<br/>
Paramètre facultatif qui définit les conventions d’appel et de nommage pour les procédures et les symboles publics.

*stackoption*<br/>
Paramètre facultatif.

*stackoption* n’est pas utilisé si *memorymodel* est `FLAT`.

La spécification de `NEARSTACK` regroupe le segment de pile dans un seul segment physique (`DGROUP`) avec les données. Le registre de segments de pile (`SS`) est supposé détenir la même adresse que le registre de segments de données (`DS`). `FARSTACK` ne regroupe pas la pile avec `DGROUP`, donc `SS` n’est pas égal à `DS`.

## <a name="remarks"></a>Notes

.`MODEL` n’est pas utilisé dans [MASM pour x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

Le tableau suivant liste les valeurs possibles pour chaque paramètre lors du ciblage des plateformes 16 bits et 32 bits :

|Paramètre|Valeurs 32 bits|Valeurs 16 bits (prise en charge du développement en 16 bits antérieur)|
|---------------|--------------------|----------------------------------------------------------------|
|*memorymodel*|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|
|*langtype*|`C`, `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|
|*stackoption*|Non utilisé|`NEARSTACK`, `FARSTACK`|

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

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>
