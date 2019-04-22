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
ms.openlocfilehash: b52c34014402a235e03c45f82dcd1e5c542e4919
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023098"
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
|`__debugbreak`|x86, ARM, x64|\<intrin.h>|

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