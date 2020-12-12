---
description: 'En savoir plus sur : CAccessor Class'
title: CAccessor, classe
ms.date: 11/04/2016
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
ms.openlocfilehash: 26b03bc3f464ce606194d6835953c39969bde5de
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319168"
---
# <a name="caccessor-class"></a>CAccessor, classe

Représente l’un des types d’accesseurs.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class CAccessor : public CAccessorBase, public T
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe d’enregistrement utilisateur.

## <a name="remarks"></a>Notes

Elle est utilisée lorsqu’un enregistrement est lié de manière statique à une source de données. L’enregistrement contient la mémoire tampon. Cette classe prend en charge plusieurs accesseurs sur un ensemble de lignes.

Utilisez ce type d’accesseur lorsque vous connaissez la structure et le type de la base de données.

Si votre accesseur contient des champs qui pointent vers la mémoire (par exemple, une `BSTR` interface ou) qui doivent être libérés, appelez la fonction membre [CAccessorRowset :: FreeRecordMemory](./caccessorrowset-class.md#freerecordmemory) avant la lecture de l’enregistrement suivant.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
