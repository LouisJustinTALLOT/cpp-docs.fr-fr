---
title: _SCL_SECURE_NO_WARNINGS
ms.date: 11/04/2016
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
ms.openlocfilehash: d19d47fe7120301740e1431765fc6edbeaa48c60
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448194"
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

L’appel de l’une des méthodes potentiellement dangereuses dans C++ la bibliothèque standard génère un [Avertissement du compilateur (niveau 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Pour désactiver cet avertissement, définissez la macro _SCL_SECURE_NO_WARNINGS dans votre code:

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

Si vous utilisez des en-têtes précompilés, placez cette directive dans votre fichier d’en-tête précompilé avant d’inclure une bibliothèque Runtime C ou des en-têtes de bibliothèque standard. Si vous le placez dans un fichier de code source individuel avant d’inclure le fichier d’en-tête précompilé, il est ignoré par le compilateur.

## <a name="remarks"></a>Notes

Autres façons de désactiver l’avertissement C4996 :

- Utilisation de l’option de compilateur [/D (définitions de préprocesseur)](../build/reference/d-preprocessor-definitions.md) :

   > CL/D_SCL_SECURE_NO_WARNINGS [autres options du compilateur] MyFile. cpp

- Utilisation de l’option de compilateur [/w](../build/reference/compiler-option-warning-level.md) :

   > CL/wd4996 [autres options du compilateur] MyFile. cpp

- Utilisation de la directive [#pragma warning](../preprocessor/warning.md) :

   ```cpp
   #pragma warning(disable:4996)
   ```

Vous pouvez aussi modifier manuellement le niveau d’avertissement C4996 avec l’option de compilateur **/w\<l>\<n>** . Par exemple, pour définir l’avertissement C4996 au niveau 4 :

> CL/w44996 [autres options du compilateur] MyFile. cpp

Pour plus d’informations, consultez [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Niveau d’avertissement)](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Voir aussi

[Bibliothèques sécurisées : Bibliothèque C++ Standard](../standard-library/safe-libraries-cpp-standard-library.md)
