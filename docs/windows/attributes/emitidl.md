---
title: emitidl (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.emitidl
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
ms.openlocfilehash: 6c4055e0f14bced1e5047fc502a4bf274126f804
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031632"
---
# <a name="emitidl"></a>emitidl

Spécifie si tous les attributs IDL suivantes sont traitées et placées dans le fichier .idl généré.

## <a name="syntax"></a>Syntaxe

```cpp
[ emitidl(state, defaultimports=boolean) ];
```

### <a name="parameters"></a>Paramètres

*état*<br/>
Une de ces valeurs possibles : `true`, `false`, `forced`, `restricted`, `push`, ou `pop`.

- Si `true`, les attributs de catégorie IDL rencontrées dans un fichier de code source sont placées dans le fichier .idl généré. Il s’agit du paramètre par défaut **emitidl**.

- Si `false`, les attributs de catégorie IDL rencontrées dans un fichier de code source ne sont pas placées dans le fichier .idl généré.

- Si `restricted`, permet des attributs IDL dans le fichier sans un [module](module-cpp.md) attribut. Le compilateur ne génère pas un fichier .idl.

- Si `forced`, remplace une ultérieure `restricted` attribut, ce qui nécessite un fichier d’avoir un `module` attribut s’il existe IDL attributs dans le fichier.

- `push` vous permet d’enregistrer actuel **emitidl** paramètres interne **emitidl** pile, et `pop` vous permet de définir **emitidl** à toute valeur s’affiche en haut de la liste interne **emitidl** pile.

`defaultimports=`*Boolean* \(facultatif)

- Si *booléenne* est **true**, docobj.idl est importé dans le fichier .idl généré. En outre, si un fichier .idl avec le même nom qu’un .h du fichier que vous avez `#include` dans votre source de code se trouve dans le même répertoire que le fichier .h, puis le fichier .idl généré contient une instruction d’importation pour ce fichier .idl.

- Si *booléenne* est **false**, docobj.idl n’est pas importé dans le fichier .idl généré. Vous devez importer explicitement les fichiers .idl avec [importer](import.md).

## <a name="remarks"></a>Notes

Après le **emitidl** attribut C++ est rencontré dans un fichier de code source, les attributs de catégorie IDL sont placés dans le fichier .idl généré. S’il existe aucune **emitidl** attribut, attributs IDL définis dans le fichier de code source sont insérées dans le fichier .idl généré.

Il est possible d’avoir plusieurs **emitidl** attributs dans un fichier de code source. Si `[emitidl(false)];` est rencontré dans un fichier sans une ultérieure `[emitidl(true)];`, aucun attribut est traitées dans le fichier .idl généré.

Chaque fois que le compilateur rencontre un nouveau fichier, **emitidl** a implicitement la valeur **true**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](compiler-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)
