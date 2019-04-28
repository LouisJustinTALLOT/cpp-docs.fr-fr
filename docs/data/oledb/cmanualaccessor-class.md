---
title: CManualAccessor, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- AddBindEntry
- CManualAccessor.AddBindEntry
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
- ATL::CManualAccessor::CreateAccessor
- CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
- ATL::CManualAccessor::CreateParameterAccessor
- ATL.CManualAccessor.CreateParameterAccessor
- CManualAccessor.CreateParameterAccessor
- CreateParameterAccessor
- CManualAccessor::CreateParameterAccessor
helpviewer_keywords:
- CManualAccessor class
- AddBindEntry method
- AddParameterEntry method
- CreateAccessor method
- CreateParameterAccessor method
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
ms.openlocfilehash: 526415f14172911b26462fab97d9e0a7513b8cad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62231062"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor, classe

Représente un type d’accesseur conçu pour une utilisation avancée.

## <a name="syntax"></a>Syntaxe

```cpp
class CManualAccessor : public CAccessorBase
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[AddBindEntry](#addbindentry)|Ajoute une entrée de liaison pour les colonnes de sortie.|
|[AddParameterEntry](#addparameterentry)|Ajoute une entrée de paramètre à l’accesseur de paramètre.|
|[CreateAccessor](#createaccessor)|Alloue de la mémoire pour la colonne des structures de liaison et initialise les membres de données de colonne.|
|[CreateParameterAccessor](#createparameteraccessor)|Alloue de la mémoire pour le paramètre de structures de liaison et initialise les membres de données de paramètre.|

## <a name="remarks"></a>Notes

À l’aide de `CManualAccessor`, vous pouvez spécifier le paramètre et liaison de colonne de sortie par des appels de fonction de l’exécution.

## <a name="addbindentry"></a> CManualAccessor::AddBindEntry

Ajoute une entrée de liaison pour les colonnes de sortie.

### <a name="syntax"></a>Syntaxe

```cpp
void AddBindEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL) throw ();
```

#### <a name="parameters"></a>Paramètres

Consultez [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) dans le *de référence du programmeur OLE DB*.

*nOrdinal*<br/>
[in] Numéro de colonne.

*wType*<br/>
[in] Type de données.

*nColumnSize*<br/>
[in] Taille de la colonne en octets.

*pData*<br/>
[in] Pointeur vers les données de colonne stockées dans la mémoire tampon.

*pLength*<br/>
[in] Pointeur vers la longueur de champ, si nécessaire.

*pStatus*<br/>
[in] Pointeur vers la variable doit être lié à l’état de la colonne, si nécessaire.

### <a name="remarks"></a>Notes

Pour utiliser cette fonction, vous devez d’abord appeler [CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md). Vous ne pouvez pas ajouter plus d’entrées que le nombre de colonnes spécifié dans `CreateAccessor`.

## <a name="addparameterentry"></a> CManualAccessor::AddParameterEntry

Ajoute une entrée de paramètre pour les structures d’entrée de paramètre.

### <a name="syntax"></a>Syntaxe

```cpp
void AddParameterEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL,
   DBPARAMIO eParamIO = DBPARAMIO_INPUT) throw ();
```

#### <a name="parameters"></a>Paramètres

Consultez [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) dans le *de référence du programmeur OLE DB*.

*nOrdinal*<br/>
[in] Numéro de paramètre.

*wType*<br/>
[in] Type de données.

*nColumnSize*<br/>
[in] Taille de la colonne en octets.

*pData*<br/>
[in] Pointeur vers les données de colonne stockées dans la mémoire tampon.

*pLength*<br/>
[in] Pointeur vers la longueur de champ, si nécessaire.

*pStatus*<br/>
[in] Pointeur vers la variable doit être lié à l’état de la colonne, si nécessaire.

*eParamIO*<br/>
[in] Spécifie si le paramètre auquel la liaison est associée est un paramètre d’entrée, d’entrée/sortie ou de sortie.

### <a name="remarks"></a>Notes

Pour utiliser cette fonction, vous devez d’abord appeler [CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md).

## <a name="createaccessor"></a> CManualAccessor::CreateAccessor

Alloue de la mémoire pour la colonne des structures de liaison et initialise les membres de données de colonne.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateAccessor(int nBindEntries,
  void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>Paramètres

*nBindEntries*<br/>
[in] Nombre de colonnes. Ce nombre doit correspondre au nombre d’appels à la [CManualAccessor::AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md) (fonction).

*pBuffer*<br/>
[in] Pointeur vers la mémoire tampon où sont stockés les colonnes de sortie.

*nBufferSize*<br/>
[in] La taille de la mémoire tampon en octets.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Appelez cette fonction avant d’appeler le `CManualAccessor::AddBindEntry` (fonction).

## <a name="createparameteraccessor"></a> CManualAccessor::CreateParameterAccessor

Alloue de la mémoire pour le paramètre de structures de liaison et initialise les membres de données de paramètre.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateParameterAccessor(int nBindEntries,
   void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>Paramètres

*nBindEntries*<br/>
[in] Nombre de colonnes.

*pBuffer*<br/>
[in] Pointeur vers la mémoire tampon où sont stockés les colonnes d’entrée.

*nBufferSize*<br/>
[in] La taille de la mémoire tampon en octets.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Vous devez appeler cette fonction avant d’appeler [AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md).

## <a name="see-also"></a>Voir aussi

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, classe](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor, classe](../../data/oledb/cdynamicparameteraccessor-class.md)