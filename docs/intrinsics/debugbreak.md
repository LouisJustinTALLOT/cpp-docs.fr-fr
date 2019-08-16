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
ms.openlocfilehash: ed75b94e8bf0aca9369c56f23e8ff00ea6953642
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509502"
---
# <a name="__debugbreak"></a>__debugbreak

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

Le `__debugbreak` compilateur intrinsèque, similaire à [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak), est un moyen portable portable de provoquer un point d’arrêt.

> [!NOTE]
>  Lors de la compilation avec **/CLR**, une `__debugbreak` fonction contenant sera compilée en langage MSIL. `asm int 3` entraîne la compilation d'une fonction en code natif. Pour plus d’informations, consultez [__asm](../assembler/inline/asm.md).

Par exemple :

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

Sur ARM64, l' `__debugbreak` intrinsèque est compilé dans l’instruction `brk #0xF000`.

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
