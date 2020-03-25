---
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
ms.openlocfilehash: 2b30cef2baf8c13c5001e44901b984aa1293494d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212301"
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

Si votre accesseur contient des champs qui pointent vers la mémoire (par exemple, une `BSTR` ou une interface) qui doivent être libérés, appelez la fonction membre [CAccessorRowset :: FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md) avant de lire l’enregistrement suivant.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
