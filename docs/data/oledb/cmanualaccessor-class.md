---
description: 'En savoir plus sur : CManualAccessor, classe'
title: CManualAccessor, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- CManualAccessor.AddBindEntry
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
- ATL::CManualAccessor::CreateAccessor
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
ms.openlocfilehash: 3d625a9a02431445cc1505c6a3f7e9673a04201d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170553"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor, classe

Représente un type d’accesseur conçu pour une utilisation avancée.

## <a name="syntax"></a>Syntaxe

```cpp
class CManualAccessor : public CAccessorBase
```

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[AddBindEntry](#addbindentry)|Ajoute une entrée de liaison aux colonnes de sortie.|
|[AddParameterEntry](#addparameterentry)|Ajoute une entrée de paramètre à l’accesseur de paramètre.|
|[CreateAccessor](#createaccessor)|Alloue de la mémoire pour les structures de liaison de colonne et initialise les membres de données de colonne.|
|[CreateParameterAccessor](#createparameteraccessor)|Alloue de la mémoire pour les structures de liaison de paramètre et initialise les membres de données de paramètre.|

## <a name="remarks"></a>Notes

À l’aide `CManualAccessor` de, vous pouvez spécifier la liaison de paramètre et de colonne de sortie par des appels de fonction au moment de l’exécution.

## <a name="cmanualaccessoraddbindentry"></a><a name="addbindentry"></a> CManualAccessor :: AddBindEntry

Ajoute une entrée de liaison aux colonnes de sortie.

### <a name="syntax"></a>Syntaxe

```cpp
void AddBindEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL) throw ();
```

#### <a name="parameters"></a>Paramètres

Consultez [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

*nOrdinal*<br/>
dans Numéro de colonne.

*wType*<br/>
dans Type de données.

*nColumnSize*<br/>
dans Taille de colonne en octets.

*pData*<br/>
dans Pointeur vers les données de colonne stockées dans la mémoire tampon.

*pLength*<br/>
dans Pointeur vers la longueur de champ, si nécessaire.

*pStatus*<br/>
dans Pointeur vers la variable à lier à l’état de colonne, si nécessaire.

### <a name="remarks"></a>Notes

Pour utiliser cette fonction, vous devez d’abord appeler [CreateAccessor](#createaccessor). Vous ne pouvez pas ajouter plus d’entrées que le nombre de colonnes spécifié dans `CreateAccessor` .

## <a name="cmanualaccessoraddparameterentry"></a><a name="addparameterentry"></a> CManualAccessor :: AddParameterEntry

Ajoute une entrée de paramètre aux structures d’entrée de paramètre.

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

Consultez [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

*nOrdinal*<br/>
dans Numéro du paramètre.

*wType*<br/>
dans Type de données.

*nColumnSize*<br/>
dans Taille de colonne en octets.

*pData*<br/>
dans Pointeur vers les données de colonne stockées dans la mémoire tampon.

*pLength*<br/>
dans Pointeur vers la longueur de champ, si nécessaire.

*pStatus*<br/>
dans Pointeur vers la variable à lier à l’état de colonne, si nécessaire.

*Affectez à eParamIO*<br/>
dans Spécifie si le paramètre auquel la liaison est associée est un paramètre d’entrée, d’entrée/sortie ou de sortie.

### <a name="remarks"></a>Notes

Pour utiliser cette fonction, vous devez d’abord appeler [CreateParameterAccessor](#createparameteraccessor).

## <a name="cmanualaccessorcreateaccessor"></a><a name="createaccessor"></a> CManualAccessor :: CreateAccessor

Alloue de la mémoire pour les structures de liaison de colonne et initialise les membres de données de colonne.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateAccessor(int nBindEntries,
  void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>Paramètres

*nBindEntries*<br/>
dans Nombre de colonnes. Ce nombre doit correspondre au nombre d’appels à la fonction [CManualAccessor :: AddBindEntry](#addbindentry) .

*pBuffer*<br/>
dans Pointeur vers la mémoire tampon dans laquelle les colonnes de sortie sont stockées.

*nBufferSize*<br/>
dans Taille de la mémoire tampon en octets.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Appelez cette fonction avant d’appeler la `CManualAccessor::AddBindEntry` fonction.

## <a name="cmanualaccessorcreateparameteraccessor"></a><a name="createparameteraccessor"></a> CManualAccessor :: CreateParameterAccessor

Alloue de la mémoire pour les structures de liaison de paramètre et initialise les membres de données de paramètre.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateParameterAccessor(int nBindEntries,
   void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>Paramètres

*nBindEntries*<br/>
dans Nombre de colonnes.

*pBuffer*<br/>
dans Pointeur vers la mémoire tampon dans laquelle les colonnes d’entrée sont stockées.

*nBufferSize*<br/>
dans Taille de la mémoire tampon en octets.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Vous devez appeler cette fonction avant d’appeler [AddParameterEntry](#addparameterentry).

## <a name="see-also"></a>Voir aussi

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, classe](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor (classe)](../../data/oledb/cdynamicparameteraccessor-class.md)
