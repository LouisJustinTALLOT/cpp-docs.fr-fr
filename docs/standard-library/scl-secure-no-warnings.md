---
description: 'En savoir plus sur : _SCL_SECURE_NO_WARNINGS'
title: _SCL_SECURE_NO_WARNINGS
ms.date: 11/04/2016
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
ms.openlocfilehash: 383aeed0bdedc4830076248100c8cf0a1acf34b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187921"
---
# <a name="_scl_secure_no_warnings"></a>_SCL_SECURE_NO_WARNINGS

L’appel de l’une des méthodes potentiellement dangereuses dans la bibliothèque standard C++ entraîne l' [Avertissement du compilateur (niveau 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Pour désactiver cet avertissement, définissez la macro _SCL_SECURE_NO_WARNINGS dans votre code :

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

En outre, vous pouvez modifier manuellement le niveau de l’avertissement C4996 avec l’option de compilateur **/w \<l> \<n>** . Par exemple, pour définir l’avertissement C4996 au niveau 4 :

> CL/w44996 [autres options du compilateur] MyFile. cpp

Pour plus d’informations, consultez [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Niveau d’avertissement)](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Voir aussi

[Bibliothèques sécurisées : bibliothèque standard C++](../standard-library/safe-libraries-cpp-standard-library.md)
