---
title: threads (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: b249eaf61266ed9964e44f6f0ad1c2f12a1b1067
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214498"
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

- `apartment` (threads cloisonnés)

- `neutral` (composants .NET Framework sans interface utilisateur)

- `single` (Threading simple)

- `free` (Threading libre)

- `both` (cloisonnement et thread libre)

La valeur par défaut est `apartment`.

## <a name="remarks"></a>Notes

L' **threading** C++ attribut de thread n’apparaît pas dans le fichier. idl généré, mais il sera utilisé dans l’implémentation de votre objet com.

Dans les projets ATL, si l’attribut [coclass](coclass.md) est également présent, le modèle de thread spécifié par le *modèle* est passé en tant que paramètre de modèle à la classe [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) , insérée par l’attribut `coclass`.

L’attribut de **thread** protège également l’accès à une [event_source](event-source.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **Threading**, consultez l’exemple [sous licence](licensed.md) .

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|**coclasse**|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Prise en charge du multithreading pour le code plus ancien (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[Cloisonnements neutres](/windows/win32/cossdk/neutral-apartments)
