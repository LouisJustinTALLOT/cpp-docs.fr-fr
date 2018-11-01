---
title: IConvertTypeImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
helpviewer_keywords:
- IConvertTypeImpl class
- CanConvert method
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
ms.openlocfilehash: dffd15478f0ae10d42b49be3b202fbd4845abb56
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544649"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl, classe

Fournit une implémentation de la [IConvertType](/previous-versions/windows/desktop/ms715926) interface.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IConvertTypeImpl
   : public IConvertType, public CConvertHelper
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IConvertTypeImpl`.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d’interface

|||
|-|-|
|[CanConvert](#canconvert)|Fournit des informations sur la disponibilité de conversions de type sur une commande ou sur un ensemble de lignes.|

## <a name="remarks"></a>Notes

Cette interface est obligatoire sur les commandes, les ensembles de lignes et les ensembles de lignes index. `IConvertTypeImpl` implémente l’interface par délégation à l’objet de conversion fourni par OLE DB.

## <a name="canconvert"></a> IConvertTypeImpl::CanConvert

Fournit des informations sur la disponibilité de conversions de type sur une commande ou sur un ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType, 
   DBTYPE wToType, 
   DBCONVERTFLAGS dwConvertFlags);
```

#### <a name="parameters"></a>Paramètres

Consultez [IConvertType::CanConvert](/previous-versions/windows/desktop/ms711224) dans le *de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Utilise la conversion de données OLE DB dans `MSADC.DLL`.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)