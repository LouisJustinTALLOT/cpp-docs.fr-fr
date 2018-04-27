---
title: _SCL_SECURE_NO_WARNINGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
dev_langs:
- C++
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5dec19d4c7d6f1def451f7f11588f303961cc5c0
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

Appel à l’une des méthodes potentiellement dangereuses dans la bibliothèque Standard C++ entraîne [l’avertissement du compilateur (niveau 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Pour désactiver cet avertissement, définissez la macro **_SCL_SECURE_NO_WARNINGS** dans votre code :

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

Si vous utilisez des en-têtes précompilés, placez cette directive dans votre fichier d’en-tête précompilé avant d’inclure n’importe quelle bibliothèque de runtime C ou en-têtes de bibliothèque standard. Si vous le placez dans un fichier de code source individuel avant d’inclure le fichier d’en-tête précompilé, il est ignoré par le compilateur.

## <a name="remarks"></a>Notes

Autres façons de désactiver l’avertissement C4996 :

- Utilisation de l’option de compilateur [/D (définitions de préprocesseur)](../build/reference/d-preprocessor-definitions.md) :

   > CL /D_SCL_SECURE_NO_WARNINGS [autres options du compilateur] myfile.cpp

- Utilisation de l’option de compilateur [/w](../build/reference/compiler-option-warning-level.md) :

   > CL /wd4996 [autres options du compilateur] myfile.cpp

- Utilisation de la directive [#pragma warning](../preprocessor/warning.md) :

   ```cpp
   #pragma warning(disable:4996)
   ```

Vous pouvez aussi modifier manuellement le niveau d’avertissement C4996 avec l’option de compilateur **/w\<l>\<n>**. Par exemple, pour définir l’avertissement C4996 au niveau 4 :

> CL /w44996 [autres options du compilateur] myfile.cpp

Pour plus d’informations, consultez [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Niveau d’avertissement)](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Voir aussi

[Bibliothèques sécurisées : bibliothèque standard C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
