---
title: uuid (C++)
ms.date: 11/04/2016
f1_keywords:
- uuid_cpp
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
ms.openlocfilehash: 09e40d38382bea0f902fda03d15d24e0cf1a627d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187802"
---
# <a name="uuid-c"></a>uuid (C++)

**Section spécifique de Microsoft**

Le compilateur attache un GUID à une classe ou une structure déclarée ou définie (définitions d’objets COM complets uniquement) avec l’attribut **UUID** .

## <a name="syntax"></a>Syntaxe

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>Notes

L’attribut **UUID** prend une chaîne comme argument. Cette chaîne désigne un GUID au format de Registre normal avec ou sans les délimiteurs **{}** . Par exemple :

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

Cet attribut peut être appliqué dans une redéclaration. Cela permet aux en-têtes du système de fournir les définitions des interfaces telles que `IUnknown`et la redéclaration dans un autre en-tête (par exemple, \<ComDef. h >) pour fournir le GUID.

Le mot clé [__uuidof](../cpp/uuidof-operator.md) peut être appliqué pour récupérer le GUID constant attaché à un type défini par l’utilisateur.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
