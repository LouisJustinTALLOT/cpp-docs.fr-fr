---
title: __addgsbyte, __addgsword, __addgsdword, __addgsqword | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __addgsdword
- __addgsqword
- __addgsword_cpp
- __addgsword
- __addgsbyte_cpp
- __addgsqword_cpp
- __addgsbyte
- __addgsdword_cpp
dev_langs:
- C++
helpviewer_keywords:
- __addgsword intrinsic
- __addgsqword intrinsic
- __addgsdword intrinsic
- __addgsbyte intrinsic
ms.assetid: 4fa03e69-d849-49ed-ba37-1d3aa23c2a21
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdfcd0db1486e5ba6e4c08dee0c19e3b98282df9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439690"
---
# <a name="addgsbyte-addgsword-addgsdword-addgsqword"></a>__addgsbyte, __addgsword, __addgsdword, __addgsqword

**Section spécifique à Microsoft**

Ajouter une valeur à un emplacement de mémoire spécifié par un offset par rapport au début de la `GS` segment.

## <a name="syntax"></a>Syntaxe

```
void __addgsbyte( 
   unsigned long Offset, 
   unsigned char Data 
);
void __addgsword( 
   unsigned long Offset, 
   unsigned short Data 
);
void __addgsdword( 
   unsigned long Offset, 
   unsigned long Data 
);
void __addgsqword( 
   unsigned long Offset, 
   unsigned __int64 Data 
);
```

#### <a name="parameters"></a>Paramètres

*Décalage*<br/>
[in] Le décalage à partir du début de `GS`.

*Données*<br/>
[in] Valeur à ajouter à l’emplacement de mémoire.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__addgsbyte`|X64|
|`__addgsword`|X64|
|`__addgsdword`|X64|
|`__addgsqword`|X64|

## <a name="remarks"></a>Notes

Ces fonctions intrinsèques sont disponibles en mode noyau uniquement, et ces routines sont uniquement disponibles en tant que fonctions intrinsèques.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__incgsbyte, \__incgsword, \__incgsdword, \__incgsqword](../intrinsics/incgsbyte-incgsword-incgsdword-incgsqword.md)<br/>
[__readgsbyte, \__readgsdword, \__readgsqword, \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)<br/>
[__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)<br/>
[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)