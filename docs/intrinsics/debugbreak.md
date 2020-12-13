---
description: 'En savoir plus sur : __debugbreak'
title: __debugbreak
ms.date: 09/02/2019
f1_keywords:
- __debugbreak_cpp
- __debugbreak
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
ms.openlocfilehash: 83a670d9fa9c1f6b41c1c405c59af71c7aa0c8a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337106"
---
# <a name="__debugbreak"></a>__debugbreak

**Spécifique à Microsoft**

Génère un point d'arrêt dans votre code, où l'utilisateur sera invité à exécuter le débogueur.

## <a name="syntax"></a>Syntaxe

```C
void __debugbreak();
```

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|En-tête|
|---------------|------------------|------------|
|`__debugbreak`|x86, x64, ARM, ARM64|\<intrin.h>|

## <a name="remarks"></a>Notes

Le `__debugbreak` compilateur intrinsèque, similaire à [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak), est un moyen portable portable de provoquer un point d’arrêt.

> [!NOTE]
> Lors de la compilation avec **/CLR**, une fonction contenant `__debugbreak` sera COMPILÉE en langage MSIL. `asm int 3` entraîne la compilation d'une fonction en code natif. Pour plus d’informations, consultez [__asm](../assembler/inline/asm.md).

Par exemple :

```C
main() {
   __debugbreak();
}
```

est similaire à :

```C
main() {
   __asm {
      int 3
   }
}
```

sur un ordinateur x86.

Sur ARM64, l' `__debugbreak` intrinsèque est compilé dans l’instruction `brk #0xF000` .

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mots clés](../cpp/keywords-cpp.md)
