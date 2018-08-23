---
title: RDX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.rdx
dev_langs:
- C++
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 423cd4585fa6e9ae5a5fbb16cf7d5c43aaf7c152
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605925"
---
# <a name="rdx"></a>rdx

Crée une clé de Registre ou modifie une clé de Registre existante.

## <a name="syntax"></a>Syntaxe

```cpp
[ rdx(
   key,
   valuename=NULL,
   regtype
) ]
```

### <a name="parameters"></a>Paramètres

*key*  
Le nom de la clé à être créé ou ouvert.

*valueName* (facultatif)  
Spécifie le champ de valeur à définir. Si un champ de valeur portant ce nom n’existe pas déjà dans la clé, il est ajouté.

*regtype*  
Le type de clé de Registre en cours d’ajout. Peut prendre l’une des opérations suivantes : `text`, `dword`, `binary`, ou `CString`.

## <a name="remarks"></a>Notes

Le **rdx** attribut C++ crée ou modifie une clé de Registre existante pour un composant COM. L’attribut ajoute une macro BEGIN_RDX_MAP à l’objet qui implémente le membre cible. `RegistryDataExchange`, une fonction injectée à la suite de la macro BEGIN_RDX_MAP, peut être utilisée pour transférer des données entre le Registre et les membres de données

Cet attribut peut être utilisé conjointement avec le [coclasse](../windows/coclass.md), [progid](../windows/progid.md), ou [vi_progid](../windows/vi-progid.md) ou les autres attributs qui implique l’un d'entre eux.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe** ou **struct** membre|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="example"></a>Exemple

Le code suivant ajoute une clé de Registre appelée MyValue pour le système qui décrit le composant COM de CMyClass.

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

[Attributs COM](../windows/com-attributes.md)  
[registration_script](../windows/registration-script.md)  