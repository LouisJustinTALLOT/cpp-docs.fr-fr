---
description: 'En savoir plus sur : RDX'
title: RDX (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.rdx
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
ms.openlocfilehash: 7d31e33bcc1883bfb787b21ec8f5c1f8bed60208
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329649"
---
# <a name="rdx"></a>rdx

Crée une clé de registre ou modifie une clé de Registre existante.

## <a name="syntax"></a>Syntaxe

```cpp
[ rdx(key, valuename=NULL, regtype) ]
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Nom de la clé à créer ou ouvrir.

*valueName*<br/>
Facultatif Spécifie le champ de valeur à définir. Si un champ de valeur portant ce nom n’existe pas déjà dans la clé, il est ajouté.

*regtype*<br/>
Type de clé de Registre ajoutée. Il peut s’agir de l’une des valeurs suivantes : `text` ,, `dword` `binary` ou `CString` .

## <a name="remarks"></a>Notes

L’attribut C++ **RDX** crée ou modifie une clé de Registre existante pour un composant com. L’attribut ajoute une macro BEGIN_RDX_MAP à l’objet qui implémente le membre cible. `RegistryDataExchange`, une fonction injectée à la suite de la macro BEGIN_RDX_MAP, peut être utilisée pour transférer des données entre le registre et les membres de données.

Cet attribut peut être utilisé conjointement avec les attributs [coclass](coclass.md), [ProgID](progid.md)ou [vi_progid](vi-progid.md) ou d’autres attributs qui impliquent l’un de ces attributs.

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`****`struct`** membre ou|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Exemple

Le code suivant ajoute une clé de Registre nommée MyValue au système décrivant le composant de modèle d’élément de configuration (CMyClass).

```cpp
// cpp_attr_ref_rdx.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include "atlbase.h"

[module (name="MyLib")];

class CMyClass {
public:
   CMyClass() {
      strcpy_s(m_sz, "SomeValue");
   }

   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]
   char m_sz[256];
};
```

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)<br/>
[registration_script](registration-script.md)
