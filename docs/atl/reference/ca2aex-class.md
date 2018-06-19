---
title: Classe de CA2AEX | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CA2AEX
- ATLCONV/ATL::CA2AEX
- ATLCONV/ATL::CA2AEX::CA2AEX
- ATLCONV/ATL::CA2AEX::m_psz
- ATLCONV/ATL::CA2AEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CA2AEX class
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdbdebb1ab79ceab44a408fc182b6037f2d32fae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358444"
---
# <a name="ca2aex-class"></a>Classe de CA2AEX
Cette classe est utilisée par les macros de conversion de chaînes `CA2TEX` et `CT2AEX`et le typedef **CA2A**.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <int t_nBufferLength = 128>
class CA2AEX
```  
  
#### <a name="parameters"></a>Paramètres  
 `t_nBufferLength`  
 La taille de la mémoire tampon utilisée dans le processus de traduction. La longueur par défaut est 128 octets.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CA2AEX::CA2AEX](#ca2aex)|Constructeur.|  
|[CA2AEX :: ~ CA2AEX](#dtor)|Destructeur.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CA2AEX::operator LPSTR](#operator_lpstr)|Opérateur de conversion.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CA2AEX::m_psz](#m_psz)|Le membre de données qui stocke la chaîne source.|  
|[CA2AEX::m_szBuffer](#m_szbuffer)|La mémoire tampon statique, utilisé pour stocker la chaîne convertie.|  
  
## <a name="remarks"></a>Notes  
 À moins que des fonctionnalités supplémentaires sont requises, utilisez `CA2TEX`, `CT2AEX`, ou **CA2A** dans votre propre code.  
  
 Cette classe contient une mémoire tampon de taille fixe statique qui est utilisé pour stocker le résultat de la conversion. Si le résultat est trop grand pour tenir dans la mémoire tampon statique, la classe alloue de la mémoire avec `malloc` et libère la mémoire quand l'objet passe en dehors de l'étendue. Cela garantit que, contrairement au texte des macros de conversion disponibles dans les versions précédentes d’ATL, cette classe est plus sûr d’utiliser dans les boucles et qu’il ne sera pas dépassement de la pile.  
  
 Si la classe tente d’allouer de la mémoire sur le tas et qu’il échoue, il appellera `AtlThrow` avec un argument de **E_OUTOFMEMORY**.  
  
 Par défaut, les macros et les classes de conversion ATL utilisent page de codes ANSI du thread actuel pour la conversion.  
  
 Les macros suivantes sont basées sur cette classe :  
  
- `CA2TEX`  
  
- `CT2AEX`  
  
 Le typedef suivant est basé sur cette classe :  
  
- **CA2A**  
  
 Pour en savoir plus sur ces macros de conversion de texte, consultez [ATL et MFC Macros de Conversion de chaînes](string-conversion-macros.md).  
  
## <a name="example"></a>Exemple  
 Consultez [ATL et MFC Macros de Conversion de chaînes](string-conversion-macros.md) pour obtenir un exemple d’utilisation de ces macros de conversion de chaînes.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlconv.h  
  
##  <a name="ca2aex"></a>  CA2AEX::CA2AEX  
 Constructeur.  
  
```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `psz`  
 La chaîne de texte à convertir.  
  
 `nCodePage`  
 Inutilisé dans cette classe.  
  
### <a name="remarks"></a>Notes  
 Crée la mémoire tampon requise pour la traduction.  
  
##  <a name="dtor"></a>  CA2AEX :: ~ CA2AEX  
 Destructeur.  
  
```
~CA2AEX() throw();
```  
  
### <a name="remarks"></a>Notes  
 Libère la mémoire tampon allouée.  
  
##  <a name="m_psz"></a>  CA2AEX::m_psz  
 Le membre de données qui stocke la chaîne source.  
  
```
LPSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>  CA2AEX::m_szBuffer  
 La mémoire tampon statique, utilisé pour stocker la chaîne convertie.  
  
```
char m_szBuffer[ t_nBufferLength];
```  
  
##  <a name="operator_lpstr"></a>  CA2AEX::operator LPSTR  
 Opérateur de conversion.  
  
```
operator LPSTR() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la chaîne de texte en tant que type **LPSTR**.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CA2CAEX](../../atl/reference/ca2caex-class.md)   
 [Classe de CA2WEX](../../atl/reference/ca2wex-class.md)   
 [Classe de CW2AEX](../../atl/reference/cw2aex-class.md)   
 [Classe de CW2CWEX](../../atl/reference/cw2cwex-class.md)   
 [Classe de CW2WEX](../../atl/reference/cw2wex-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)