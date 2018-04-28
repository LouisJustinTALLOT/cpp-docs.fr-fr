---
title: . MODÈLE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .MODEL
dev_langs:
- C++
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2814b1b6cc4483807f77989ff4fbb70929400d6e
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
---
# <a name="model"></a>.MODEL
Initialise le modèle de mémoire programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.MODEL memorymodel [[, langtype]] [[, stackoption]]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `memorymodel`  
 Paramètre obligatoire qui détermine la taille des pointeurs de code et les données.  
  
 `langtype`  
 Paramètre facultatif qui définit les conventions d’appel et d’affectation de noms des procédures et des symboles publics.  
  
 `stackoption`  
 Paramètre facultatif.  
  
 `stackoption` n’est pas utilisé si `memorymodel` est `FLAT`.  
  
 Spécification de `NEARSTACK` regroupe le segment de pile dans un unique segment physique (`DGROUP`), ainsi que des données. Le Registre de segment de pile (`SS`) est supposée pour contenir la même adresse que le Registre de segment de données (`DS`). `FARSTACK` ne regroupe pas de la pile avec `DGROUP`; par conséquent `SS` n’est pas égale `DS`.  
  
## <a name="remarks"></a>Notes  
 .`MODEL` n’est pas utilisé dans [MASM pour x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
 Le tableau suivant répertorie les valeurs possibles pour chaque paramètre lors du ciblage de plateformes de 16 bits et 32 bits :  
  
|Paramètre|valeurs 32 bits|valeurs de 16 bits (prise en charge pour le développement de 16 bits antérieur)|  
|---------------|--------------------|----------------------------------------------------------------|  
|`memorymodel`|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|  
|`langtype`|`C`, `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|  
|`stackoption`|Non utilisé|`NEARSTACK`, `FARSTACK`|  
  
## <a name="code"></a>Code  
 Pour obtenir des exemples liés MASM, téléchargez les exemples de compilateur de [exemples Visual C++ et sa Documentation pour Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=178749).  
  
 L’exemple suivant illustre l’utilisation de la `.MODEL` la directive.  
  
## <a name="example"></a>Exemple  
  
```  
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
 [Référence des directives](../../assembler/masm/directives-reference.md)   
 [Exemples Visual C++ et sa Documentation pour Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=178749)