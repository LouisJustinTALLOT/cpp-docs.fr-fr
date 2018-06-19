---
title: Classe de CA2CAEX | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
dev_langs:
- C++
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8aa16122a1cb3a5f8378397363a45cd28ddaef6d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357800"
---
# <a name="ca2caex-class"></a>Classe de CA2CAEX
Cette classe est utilisée par les macros de conversion de chaînes `CA2CTEX` et `CT2CAEX`et le typedef **CA2CA**.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<int t_nBufferLength = 128>  
class CA2CAEX
```  
  
#### <a name="parameters"></a>Paramètres  
 `t_nBufferLength`  
 La taille de la mémoire tampon utilisée dans le processus de traduction. La longueur par défaut est 128 octets.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CA2CAEX::CA2CAEX](#ca2caex)|Constructeur.|  
|[CA2CAEX :: ~ CA2CAEX](#dtor)|Destructeur.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CA2CAEX::operator LPCSTR](#operator_lpcstr)|Opérateur de conversion.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CA2CAEX::m_psz](#m_psz)|Le membre de données qui stocke la chaîne source.|  
  
## <a name="remarks"></a>Notes  
 À moins que des fonctionnalités supplémentaires sont requises, utilisez `CA2CTEX`, `CT2CAEX`, ou **CA2CA** dans votre propre code.  
  
 Cette classe est plus sûr d’utiliser dans les boucles et ne sera pas dépassement de la pile. Par défaut, les classes et macros de conversion ATL utilisent la page de codes ANSI du thread actif pour la conversion.  
  
 Les macros suivantes sont basées sur cette classe :  
  
- `CA2CTEX`  
  
- `CT2CAEX`  
  
 Le typedef suivant est basé sur cette classe :  
  
- **CA2CA**  
  
 Pour en savoir plus sur ces macros de conversion de texte, consultez [ATL et MFC Macros de Conversion de chaînes](string-conversion-macros.md).  
  
## <a name="example"></a>Exemple  
 Consultez [ATL et MFC Macros de Conversion de chaînes](string-conversion-macros.md) pour obtenir un exemple d’utilisation de ces macros de conversion de chaînes.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlconv.h  
  
##  <a name="ca2caex"></a>  CA2CAEX::CA2CAEX  
 Constructeur.  
  
```
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `psz`  
 La chaîne de texte à convertir.  
  
 `nCodePage`  
 Inutilisé dans cette classe.  
  
### <a name="remarks"></a>Notes  
 Crée la mémoire tampon requise pour la traduction.  
  
##  <a name="dtor"></a>  CA2CAEX :: ~ CA2CAEX  
 Destructeur.  
  
```
~CA2CAEX() throw();
```  
  
### <a name="remarks"></a>Notes  
 Libère la mémoire tampon allouée.  
  
##  <a name="m_psz"></a>  CA2CAEX::m_psz  
 Le membre de données qui stocke la chaîne source.  
  
```
LPCSTR m_psz;
```  
  
##  <a name="operator_lpcstr"></a>  CA2CAEX::operator LPCSTR  
 Opérateur de conversion.  
  
```  
operator LPCSTR() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la chaîne de texte en tant que type `LPCSTR`.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CA2AEX](../../atl/reference/ca2aex-class.md)   
 [Classe de CA2WEX](../../atl/reference/ca2wex-class.md)   
 [Classe de CW2AEX](../../atl/reference/cw2aex-class.md)   
 [Classe de CW2CWEX](../../atl/reference/cw2cwex-class.md)   
 [Classe de CW2WEX](../../atl/reference/cw2wex-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
