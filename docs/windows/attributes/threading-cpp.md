---
title: Threading (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: cdebf06a62ebbd1d8648b9777fe200bc7a373261
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038276"
---
# <a name="threading-c"></a>thread (C++)

Spécifie le modèle de thread pour un objet COM.

## <a name="syntax"></a>Syntaxe

```cpp
[ threading(model=enumeration) ]
```

### <a name="parameters"></a>Paramètres

*modèle*<br/>
(Facultatif) L’un des modèles de threads suivants :

- `apartment` (modèle de thread cloisonné)

- `neutral` (Composants de .NET framework sans interface utilisateur)

- `single` (thread simple)

- `free` (threading libre)

- `both` (cloisonnement et modèle de thread libre)

La valeur par défaut est `apartment`.

## <a name="remarks"></a>Notes

Le **threading** attribut C++ n’apparaît pas dans le fichier .idl généré, mais sera utilisé dans l’implémentation de votre objet COM.

Dans les projets ATL, si le [coclasse](coclass.md) attribut est également présent, le modèle de thread spécifié par *modèle* est passé comme paramètre de modèle pour le [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) classe , inséré par la `coclass` attribut.

Le **threading** attribut protège également l’accès à un [event_source](event-source.md).

## <a name="example"></a>Exemple

Consultez le [concédé sous licence](licensed.md) exemple pour un exemple d’utilisation de **threading**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**class**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|**coclasse**|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Prise en charge du multithreading pour le code plus ancien (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[Cloisonnements neutres](/windows/desktop/cossdk/neutral-apartments)