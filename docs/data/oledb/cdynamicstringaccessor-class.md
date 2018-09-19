---
title: CDynamicStringAccessor, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessor
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessor class
- GetString method
- SetString method
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0af37ee6f76e5a9e3b6423023fbe2691392395de
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044117"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor, classe

Vous permet d’accéder à une source de données lorsque vous n’avez aucune connaissance du schéma de base de données (structure sous-jacente de la base de données).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
template< typename BaseType, DBTYPEENUM OleDbType >  
class CDynamicStringAccessorT : public CDynamicAccessor  
```  

## <a name="requirements"></a>Configuration requise  

**En-tête**: atldbcli.h 

## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[GetString](#getstring)|Récupère les données de la colonne spécifiée sous forme de chaîne.|  
|[SetString](#setstring)|Définit les données de la colonne spécifiée sous forme de chaîne.|  
  
## <a name="remarks"></a>Notes  

Bien que [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) demande des données dans le format natif indiqué par le fournisseur, `CDynamicStringAccessor` demande que le fournisseur récupère toutes les données accessibles à partir du magasin de données en tant que données de chaîne. Cela est particulièrement utile pour des tâches simples qui ne nécessitent pas de calcul de valeurs dans le magasin de données, telles que l’affichage ou l’impression du contenu du magasin de données.  
  
Le type natif des données de colonne dans le magasin de données n’a pas d’importance ; tant que le fournisseur peut prendre en charge la conversion de données, il fournit les données au format de chaîne. Si le fournisseur ne prend pas en charge la conversion du type de données natif en une chaîne (qui n’est pas courant), l’appel de demande renvoie la valeur de réussite DB_S_ERRORSOCCURED, et l’état de la colonne correspondante indique un problème de conversion DBSTATUS_E_CANTCONVERTVALUE.  
  
Utilisez `CDynamicStringAccessor` méthodes pour obtenir des informations de colonne. Ces informations de colonne vous permet de créer un accesseur dynamiquement au moment de l’exécution.  
  
Les informations de colonne sont stockées dans une mémoire tampon créée et gérée par cette classe. Obtenir des données à partir de la mémoire tampon à l’aide [GetString](../../data/oledb/cdynamicstringaccessor-getstring.md), ou les stocker dans la mémoire tampon à l’aide [SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).  
  
Pour une discussion et des exemples d’utilisation des classes d’accesseurs dynamiques, consultez [à l’aide d’accesseurs dynamiques](../../data/oledb/using-dynamic-accessors.md).  

## <a name="getstring"></a> CDynamicStringAccessor::GetString

Récupère les données de la colonne spécifiée sous forme de chaîne.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();  

BaseType* GetString(const CHAR* pColumnName) const throw();  

BaseType* GetString(const WCHAR* pColumnName) const throw();  
```  
  
#### <a name="parameters"></a>Paramètres  

*nColumn*<br/>
[in] Le numéro de colonne. Les numéros de colonne commencent à 1. La valeur 0 fait référence à la colonne de signet, le cas échéant.  
  
*pColumnName*<br/>
[in] Pointeur vers une chaîne de caractères qui contient le nom de colonne.  
  
### <a name="return-value"></a>Valeur de retour  

Un pointeur vers la valeur de chaîne sont extraites de la colonne spécifiée. La valeur est de type `BaseType`, qui sera **CHAR** ou **WCHAR** selon que _UNICODE est défini ou non. Retourne NULL si la colonne spécifiée est introuvable.  
  
### <a name="remarks"></a>Notes  

Le deuxième remplacement formulaire prend le nom de colonne sous forme de chaîne ANSI. La troisième remplacer formulaire prend le nom de colonne sous forme de chaîne Unicode.  
 
## <a name="setstring"></a> CDynamicStringAccessor::SetString

Définit les données de la colonne spécifiée sous forme de chaîne.  
  
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
[in] Le numéro de colonne. Les numéros de colonne commencent à 1. La valeur spéciale 0 fait référence à la colonne de signet, le cas échéant.  
  
*pColumnName*<br/>
[in] Pointeur vers une chaîne de caractères qui contient le nom de colonne.  
  
*data*<br/>
[in] Pointeur vers les données de chaîne à écrire dans la colonne spécifiée.  
  
### <a name="return-value"></a>Valeur de retour  

Pointeur vers la valeur de chaîne à laquelle définir la colonne spécifiée. La valeur est de type `BaseType`, qui sera **CHAR** ou **WCHAR** selon que _UNICODE est défini ou non.  
  
### <a name="remarks"></a>Notes  

La seconde substituer formulaire prend le nom de colonne sous forme de chaîne ANSI ainsi le troisième formulaire prend le nom de colonne sous forme de chaîne Unicode.  
  
Si _SECURE_ATL est défini comme ayant une valeur différente de zéro, un échec d’assertion runtime sera généré si l’entrée *données* chaîne est plus longue que la longueur maximale autorisée de la colonne de données référencé. Sinon, la chaîne d’entrée sera être tronquée si elle est supérieure à la longueur maximale autorisée.  
  
## <a name="see-also"></a>Voir aussi  

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, classe](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor, classe](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor, classe](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessorA, classe](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW, classe](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CXMLAccessor, classe](../../data/oledb/cxmlaccessor-class.md)