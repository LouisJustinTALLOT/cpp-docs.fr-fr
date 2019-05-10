---
title: uuid (attributs C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: eae79f9a4d0af6375834c0792c4004f52a16e07e
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448926"
---
# <a name="uuid-c-attributes"></a>uuid (attributs C++)

Spécifie l’ID unique pour une classe ou interface.

## <a name="syntax"></a>Syntaxe

```cpp
[ uuid(
   "uuid"
) ]
```

### <a name="parameters"></a>Paramètres

*uuid*<br/>
Identificateur unique de 128 bits.

## <a name="remarks"></a>Notes

Si la définition d’une interface ou une classe ne spécifie pas le **uuid** C++ attribut, puis Microsoft C++ compilateur fournira une. Lorsque vous spécifiez un **uuid**, vous devez inclure les guillemets.

Si vous ne spécifiez pas **uuid**, le compilateur génère le même GUID pour les interfaces ou classes portant le même nom dans les projets d’attributs différentes sur un ordinateur.

Vous pouvez utiliser Uuidgen.exe ou Guidgen.exe pour générer votre propre ID unique. (Pour exécuter un de ces outils, cliquez sur **Démarrer** et cliquez sur **exécuter** dans le menu. Entrez le nom de l’outil requis.)

Lorsqu’il est utilisé dans un projet qui n’utilise pas également ATL, en spécifiant le **uuid** attribut est le même que si vous définissiez le [uuid](../../cpp/uuid-cpp.md) **__declspec** modificateur. Pour récupérer le **uuid** d’une classe, vous pouvez utiliser [__uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>Exemple

Consultez le [peut être liée](bindable.md) exemple pour un exemple d’utilisation de **uuid**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**class**, **struct**, **interface**, **union**, **enum**|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/desktop/Midl/uuid)