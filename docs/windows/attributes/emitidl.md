---
title: emitidl (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.emitidl
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
ms.openlocfilehash: 32362f287320e69d1680cbe07ca050143b507514
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846327"
---
# <a name="emitidl"></a>emitidl

Spécifie si tous les attributs IDL suivants sont traités et placés dans le fichier. idl généré.

## <a name="syntax"></a>Syntaxe

```cpp
[ emitidl(state, defaultimports=boolean) ];
```

### <a name="parameters"></a>Paramètres

*state*<br/>
Une de ces valeurs possibles : **`true`** , **`false`** , `forced` , `restricted` , `push` ou `pop` .

- Si **`true`** , tous les attributs de catégorie IDL rencontrés dans un fichier de code source sont placés dans le fichier. idl généré. Il s’agit du paramètre par défaut pour **emitidl**.

- Si **`false`** la condition est, tous les attributs de catégorie IDL rencontrés dans un fichier de code source ne sont pas placés dans le fichier. idl généré.

- Si `restricted` la valeur est, permet aux attributs IDL d’être dans le fichier sans attribut de [module](module-cpp.md) . Le compilateur ne génère pas de fichier. idl.

- Si `forced` , remplace un `restricted` attribut suivant, qui requiert qu’un fichier ait un `module` attribut s’il existe des attributs IDL dans le fichier.

- `push` vous permet d’enregistrer les paramètres **emitidl** actuels dans une pile **emitidl** interne et `pop` vous permet de définir **emitidl** sur la valeur qui se trouve en haut de la pile **emitidl** interne.

`defaultimports=`*valeur booléenne* \( facultatif

- Si la *valeur booléenne* est **`true`** , docobj. idl est importé dans le fichier. idl généré. En outre, si un fichier. idl portant le même nom qu’un fichier. h dans `#include` votre code source se trouve dans le même répertoire que le fichier. h, le fichier. idl généré contient une instruction import pour ce fichier. idl.

- Si la *valeur booléenne* est **`false`** , docobj. idl n’est pas importé dans le fichier. idl généré. Vous devez importer explicitement des fichiers. idl avec [Import](import.md).

## <a name="remarks"></a>Notes

Une fois l’attribut C++ **emitidl** trouvé dans un fichier de code source, les attributs de catégorie IDL sont placés dans le fichier. idl généré. S’il n’existe aucun attribut **emitidl** , les attributs IDL dans le fichier de code source sont générés dans le fichier. idl généré.

Il est possible d’avoir plusieurs attributs **emitidl** dans un fichier de code source. Si `[emitidl(false)];` est rencontré dans un fichier sans un autre `[emitidl(true)];` , aucun attribut n’est alors traité dans le fichier. idl généré.

Chaque fois que le compilateur rencontre un nouveau fichier, **emitidl** est implicitement défini sur **`true`** .

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|N'importe où|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du compilateur](compiler-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)
