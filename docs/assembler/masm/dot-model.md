---
title: .MODEL
ms.date: 08/30/2018
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: 5c7d5a1cfe16ef3cb1d79617133cd1ceccdfb78c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633507"
---
# <a name="model"></a>.MODEL

Initialise le modèle de mémoire programme.

## <a name="syntax"></a>Syntaxe

> . MODÈLE memorymodel [[, langtype]] [[, stackoption]]

### <a name="parameters"></a>Paramètres

*memoryModel*<br/>
Paramètre obligatoire qui détermine la taille des pointeurs de code et les données.

*langtype*<br/>
Paramètre facultatif qui définit les conventions d’appel et d’affectation de noms pour les procédures et les symboles publics.

*stackoption*<br/>
Paramètre facultatif.

*stackoption* n’est pas utilisé si *memorymodel* est `FLAT`.

Spécification `NEARSTACK` regroupe le segment de pile dans un seul segment physique (`DGROUP`), ainsi que des données. Le Registre de segment de pile (`SS`) est supposée pour contenir la même adresse que le Registre de segment de données (`DS`). `FARSTACK` ne regroupe pas de la pile avec `DGROUP`; par conséquent `SS` n’est pas égal `DS`.

## <a name="remarks"></a>Notes

.`MODEL` n’est pas utilisé dans [MASM pour x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

Le tableau suivant répertorie les valeurs possibles pour chaque paramètre lors du ciblage de plateformes 16 bits et 32 bits :

|Paramètre|valeurs 32 bits|valeurs 16 bits (prise en charge pour le développement de 16 bits antérieures)|
|---------------|--------------------|----------------------------------------------------------------|
|*memoryModel*|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|
|*langtype*|`C`, `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|
|*stackoption*|Non utilisé|`NEARSTACK`, `FARSTACK`|

## <a name="code"></a>Code

Pour obtenir des exemples liés à MASM, télécharger les exemples de compilateur à [exemples Visual C++ et sa Documentation pour Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=178749).

L’exemple suivant illustre l’utilisation de la `.MODEL` directive.

## <a name="example"></a>Exemple

```asm
; file simple.asm
; For x86 (32-bit), assemble with debug information:
;   ml -c -Zi simple.asm
; For x64 (64-bit), assemble with debug information:
;   ml64 -c -DX64 -Zi simple.asm
;
; In this sample, the 'X64' define excludes source not used
;  when targeting the x64 architecture

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

