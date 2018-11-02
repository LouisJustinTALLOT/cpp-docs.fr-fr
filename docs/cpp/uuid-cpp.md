---
title: uuid (C++)
ms.date: 11/04/2016
f1_keywords:
- uuid_cpp
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
ms.openlocfilehash: c121ad99dfbe0021a263f324ccdb9a95441bba33
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511655"
---
# <a name="uuid-c"></a>uuid (C++)

**Section spécifique à Microsoft**

Le compilateur attache un GUID à une classe ou une structure déclarée ou définie (COM objet définitions complètes uniquement) avec le **uuid** attribut.

## <a name="syntax"></a>Syntaxe

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>Notes

Le **uuid** attribut prend une chaîne comme argument. Cette chaîne de nom à un GUID au format normal de Registre avec ou sans le **{}** délimiteurs. Exemple :

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

Cet attribut peut être appliqué dans une redéclaration. Ainsi, les en-têtes système fournir les définitions des interfaces telles que `IUnknown`et la redéclaration dans un autre en-tête (tel que \<comdef.h >) pour fournir un GUID.

Le mot clé [__uuidof](../cpp/uuidof-operator.md) peut être appliqué pour récupérer le GUID constant attaché à un type défini par l’utilisateur.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)