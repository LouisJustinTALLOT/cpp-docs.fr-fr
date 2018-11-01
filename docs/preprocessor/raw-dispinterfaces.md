---
title: raw_dispinterfaces
ms.date: 11/04/2016
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: 8a6c335c7afe2cc56613f06abf5c181f05f6bfec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585391"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**Spécifique à C++**

Indique au compilateur de générer des fonctions wrapper de bas niveau pour dispinterface méthodes et propriétés qui appellent `IDispatch::Invoke` et renvoyer le code d’erreur HRESULT.

## <a name="syntax"></a>Syntaxe

```
raw_dispinterfaces
```

## <a name="remarks"></a>Notes

Si cet attribut n'est pas spécifié, seuls sont générés les wrappers de niveau supérieur, qui lèvent des exceptions C++ en cas d'échec.

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)