---
description: 'En savoir plus sur : Threading (C++)'
title: threads (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: e46a3720280fe7ee7b9debae98e3270825e8db40
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327254"
---
# <a name="threading-c"></a>thread (C++)

Spécifie le modèle de thread pour un objet COM.

## <a name="syntax"></a>Syntaxe

```cpp
[ threading(model=enumeration) ]
```

### <a name="parameters"></a>Paramètres

*model*<br/>
Facultatif L’un des modèles de thread suivants :

- `apartment` (thread cloisonné)

- `neutral` (Composants .NET Framework sans interface utilisateur)

- `single` (thread simple)

- `free` (Threading libre)

- `both` (cloisonnement et threads libres)

La valeur par défaut est `apartment`.

## <a name="remarks"></a>Notes

L’attribut **Threading** C++ n’apparaît pas dans le fichier. idl généré, mais il sera utilisé dans l’implémentation de votre objet com.

Dans les projets ATL, si l’attribut [coclass](coclass.md) est également présent, le modèle de thread spécifié par le *modèle* est passé en tant que paramètre de modèle à la classe [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) , insérée par l' `coclass` attribut.

L’attribut de **thread** protège également l’accès à une [event_source](event-source.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **Threading**, consultez l’exemple [sous licence](licensed.md) .

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`**, **`struct`**|
|**Renouvelable**|Non|
|**Attributs requis**|**coclasse**|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Prise en charge du multithreading pour le code plus ancien (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[Cloisonnements neutres](/windows/win32/cossdk/neutral-apartments)
