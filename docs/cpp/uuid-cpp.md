---
title: uuid (C++)
ms.date: 11/04/2016
f1_keywords:
- uuid_cpp
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
ms.openlocfilehash: f775820fe7f84c5081a213ca9ecb07d617716a9d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226982"
---
# <a name="uuid-c"></a>uuid (C++)

**Spécifique à Microsoft**

Le compilateur attache un GUID à une classe ou une structure déclarée ou définie (définitions d’objets COM complets uniquement) avec l' **`uuid`** attribut.

## <a name="syntax"></a>Syntaxe

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>Notes

L' **`uuid`** attribut prend une chaîne comme argument. Cette chaîne désigne un GUID au format de Registre normal avec ou sans les délimiteurs **{}** . Par exemple :

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

Cet attribut peut être appliqué dans une redéclaration. Cela permet aux en-têtes du système de fournir les définitions des interfaces telles que `IUnknown` , et la redéclaration dans un autre en-tête (tel que \<comdef.h> ) pour fournir le GUID.

Le mot clé [__uuidof](../cpp/uuidof-operator.md) peut être appliqué pour récupérer le GUID constant attaché à un type défini par l’utilisateur.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
