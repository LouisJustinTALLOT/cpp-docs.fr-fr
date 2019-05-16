---
title: __debugbreak
ms.date: 11/04/2016
f1_keywords:
- __debugbreak_cpp
- __debugbreak
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
ms.openlocfilehash: 8e5d53998b6ca37d2f60e9b86aed8df07c256ded
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708191"
---
# <a name="debugbreak"></a>__debugbreak

**Section spécifique à Microsoft**

Génère un point d'arrêt dans votre code, où l'utilisateur sera invité à exécuter le débogueur.

## <a name="syntax"></a>Syntaxe

```
void __debugbreak();
```

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|Header|
|---------------|------------------|------------|
|`__debugbreak`|x86, x64, ARM, ARM64|\<intrin.h>|

## <a name="remarks"></a>Notes

Le `__debugbreak` compilateur intrinsèque, comme dans [DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297.aspx), est une manière Win32 portable pour provoquer un point d’arrêt.

> [!NOTE]
>  Lors de la compilation avec **/CLR**, une fonction contenant `__debugbreak` seront compilés en MSIL. `asm int 3` entraîne la compilation d'une fonction en code natif. Pour plus d’informations, consultez [__asm](../assembler/inline/asm.md).

Exemple :

```
main() {
   __debugbreak();
}
```

est similaire à :

```
main() {
   __asm {
      int 3
   }
}
```

sur un ordinateur x86.

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
