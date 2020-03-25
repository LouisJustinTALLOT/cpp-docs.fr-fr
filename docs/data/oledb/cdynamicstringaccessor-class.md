---
title: CDynamicStringAccessor, classe
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessor
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
helpviewer_keywords:
- CDynamicStringAccessor class
- GetString method
- SetString method
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
ms.openlocfilehash: a0590bc015c5487315b8cbd38f0baf91eb3082cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211862"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor, classe

Vous permet d’accéder à une source de données lorsque vous n’avez aucune connaissance du schéma de base de données (la structure sous-jacente de la base de données).

## <a name="syntax"></a>Syntaxe

```cpp
template< typename BaseType, DBTYPEENUM OleDbType >
class CDynamicStringAccessorT : public CDynamicAccessor
```

## <a name="requirements"></a>Spécifications

**En-tête**: atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[GetString](#getstring)|Récupère les données de colonne spécifiées sous la forme d’une chaîne.|
|[SetString](#setstring)|Définit les données de colonne spécifiées sous la forme d’une chaîne.|

## <a name="remarks"></a>Notes

Si [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) demande des données au format natif signalé par le fournisseur, `CDynamicStringAccessor` demande au fournisseur d’extraire toutes les données accessibles à partir du magasin de données en tant que données de chaîne. Cela s’avère particulièrement utile pour les tâches simples qui ne nécessitent pas de calcul de valeurs dans le magasin de données, telles que l’affichage ou l’impression du contenu du magasin de données.

Le type natif des données de colonne dans le magasin de données n’a pas d’importance ; tant que le fournisseur peut prendre en charge la conversion de données, il fournit les données au format de chaîne. Si le fournisseur ne prend pas en charge la conversion du type de données natif en une chaîne (ce qui n’est pas courant), l’appel demandeur retourne la valeur de réussite DB_S_ERRORSOCCURED, et l’état de la colonne correspondante indique un problème de conversion avec DBSTATUS_E_CANTCONVERTVALUE.

Utilisez `CDynamicStringAccessor` méthodes pour obtenir des informations sur les colonnes. Vous utilisez ces informations de colonne pour créer un accesseur de manière dynamique au moment de l’exécution.

Les informations de colonne sont stockées dans une mémoire tampon créée et gérée par cette classe. Obtenez des données à partir de la mémoire tampon à l’aide de [GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)ou stockez-les dans la mémoire tampon à l’aide de [SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).

Pour obtenir une discussion et des exemples d’utilisation des classes d’accesseur dynamiques, consultez [utilisation d’accesseurs dynamiques](../../data/oledb/using-dynamic-accessors.md).

## <a name="cdynamicstringaccessorgetstring"></a><a name="getstring"></a>CDynamicStringAccessor :: GetString

Récupère les données de colonne spécifiées sous la forme d’une chaîne.

### <a name="syntax"></a>Syntaxe

```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();

BaseType* GetString(const CHAR* pColumnName) const throw();

BaseType* GetString(const WCHAR* pColumnName) const throw();
```

#### <a name="parameters"></a>Paramètres

*nColumn*<br/>
dans Numéro de la colonne. Les numéros de colonne commencent par 1. La valeur 0 fait référence à la colonne de signets, le cas échéant.

*pColumnName*<br/>
dans Pointeur vers une chaîne de caractères qui contient le nom de la colonne.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la valeur de chaîne Récupérée à partir de la colonne spécifiée. La valeur est de type `BaseType`, qui sera **char** ou **WCHAR** selon que _UNICODE est défini ou non. Retourne la valeur NULL si la colonne spécifiée est introuvable.

### <a name="remarks"></a>Notes

Le deuxième formulaire de remplacement prend le nom de colonne comme une chaîne ANSI. Le troisième formulaire de remplacement prend le nom de colonne en tant que chaîne Unicode.

## <a name="cdynamicstringaccessorsetstring"></a><a name="setstring"></a>CDynamicStringAccessor :: SetString

Définit les données de colonne spécifiées sous la forme d’une chaîne.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetString(DBORDINAL nColumn,
   BaseType* data) throw();

HRESULT SetString(const CHAR* pColumnName,
   BaseType* data) throw();

HRESULT SetString(const WCHAR* pColumnName,
   BaseType* data) throw();
```

#### <a name="parameters"></a>Paramètres

*nColumn*<br/>
dans Numéro de la colonne. Les numéros de colonne commencent par 1. La valeur spéciale 0 fait référence à la colonne de signets, le cas échéant.

*pColumnName*<br/>
dans Pointeur vers une chaîne de caractères qui contient le nom de la colonne.

*data*<br/>
dans Pointeur vers les données de chaîne à écrire dans la colonne spécifiée.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la valeur de chaîne dans laquelle définir la colonne spécifiée. La valeur est de type `BaseType`, qui sera **char** ou **WCHAR** selon que _UNICODE est défini ou non.

### <a name="remarks"></a>Notes

Le deuxième formulaire de remplacement prend le nom de colonne comme une chaîne ANSI et le troisième formulaire de remplacement prend le nom de colonne en tant que chaîne Unicode.

Si _SECURE_ATL est défini pour avoir une valeur différente de zéro, un échec d’assertion de Runtime est généré si la chaîne de *données* d’entrée dépasse la longueur maximale autorisée de la colonne de données référencée. Dans le cas contraire, la chaîne d’entrée sera tronquée si elle dépasse la longueur maximale autorisée.

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, classe](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor, classe](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor, classe](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessorA, classe](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW, classe](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CXMLAccessor, classe](../../data/oledb/cxmlaccessor-class.md)
