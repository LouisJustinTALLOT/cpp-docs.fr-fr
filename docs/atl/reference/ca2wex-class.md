---
title: Classe de CA2WEX | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 218e0d8f5e93a9e6c41ff855ff086cc7bfa6c766
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358744"
---
# <a name="ca2wex-class"></a>Classe de CA2WEX
Cette classe est utilisée par les macros de conversion de chaînes `CA2TEX`, `CA2CTEX`, `CT2WEX`, et `CT2CWEX`et le typedef **CA2W**.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <int t_nBufferLength = 128>
class CA2WEX
```  
  
#### <a name="parameters"></a>Paramètres  
 `t_nBufferLength`  
 La taille de la mémoire tampon utilisée dans le processus de traduction. La longueur par défaut est 128 octets.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CA2WEX::CA2WEX](#ca2wex)|Constructeur.|  
|[CA2WEX :: ~ CA2WEX](#dtor)|Destructeur.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CA2WEX::operator LPWSTR](#operator_lpwstr)|Opérateur de conversion.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CA2WEX::m_psz](#m_psz)|Le membre de données qui stocke la chaîne source.|  
|[CA2WEX::m_szBuffer](#m_szbuffer)|La mémoire tampon statique, utilisé pour stocker la chaîne convertie.|  
  
## <a name="remarks"></a>Notes  
 À moins que des fonctionnalités supplémentaires sont requises, utilisez `CA2TEX`, `CA2CTEX`, `CT2WEX`, `CT2CWEX`, ou **CA2W** dans votre code.  
  
 Cette classe contient une mémoire tampon de taille fixe statique qui est utilisé pour stocker le résultat de la conversion. Si le résultat est trop grand pour tenir dans la mémoire tampon statique, la classe alloue de la mémoire avec `malloc` et libère la mémoire quand l'objet passe en dehors de l'étendue. Cela garantit que, contrairement au texte des macros de conversion disponibles dans les versions précédentes d’ATL, cette classe est plus sûr d’utiliser dans les boucles et qu’il ne sera pas dépassement de la pile.  
  
 Si la classe tente d’allouer de la mémoire sur le tas et qu’il échoue, il appellera `AtlThrow` avec un argument de **E_OUTOFMEMORY**.  
  
 Par défaut, les macros et les classes de conversion ATL utilisent page de codes ANSI du thread actuel pour la conversion. Si vous souhaitez substituer ce comportement pour une conversion spécifique, spécifiez la page de codes comme second paramètre au constructeur de la classe.  
  
 Les macros suivantes sont basées sur cette classe :  
  
- `CA2TEX`  
  
- `CA2CTEX`  
  
- `CT2WEX`  
  
- `CT2CWEX`  
  
 Le typedef suivant est basé sur cette classe :  
  
- **CA2W**  
  
 Pour en savoir plus sur ces macros de conversion de texte, consultez [ATL et MFC Macros de Conversion de chaînes](string-conversion-macros.md).  
  
## <a name="example"></a>Exemple  
 Consultez [ATL et MFC Macros de Conversion de chaînes](string-conversion-macros.md) pour obtenir un exemple d’utilisation de ces macros de conversion de chaînes.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlconv.h  
  
##  <a name="ca2wex"></a>  CA2WEX::CA2WEX  
 Constructeur.  
  
```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `psz`  
 La chaîne de texte à convertir.  
  
 `nCodePage`  
 La page de codes utilisée pour effectuer la conversion. Consultez la discussion de paramètre de page de code pour la fonction du Kit de développement logiciel Windows [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072) pour plus d’informations.  
  
### <a name="remarks"></a>Notes  
 Alloue de la mémoire tampon utilisée dans le processus de traduction.  
  
##  <a name="dtor"></a>  CA2WEX :: ~ CA2WEX  
 Destructeur.  
  
```
~CA2WEX() throw();
```  
  
### <a name="remarks"></a>Notes  
 Libère la mémoire tampon allouée.  
  
##  <a name="m_psz"></a>  CA2WEX::m_psz  
 Le membre de données qui stocke la chaîne source.  
  
```
LPWSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>  CA2WEX::m_szBuffer  
 La mémoire tampon statique, utilisé pour stocker la chaîne convertie.  
  
```
wchar_t m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpwstr"></a>  CA2WEX::operator LPWSTR  
 Opérateur de conversion.  
  
```  
operator LPWSTR() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la chaîne de texte en tant que type **LPWSTR.**  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CA2AEX](../../atl/reference/ca2aex-class.md)   
 [Classe de CA2CAEX](../../atl/reference/ca2caex-class.md)   
 [Classe de CW2AEX](../../atl/reference/cw2aex-class.md)   
 [Classe de CW2CWEX](../../atl/reference/cw2cwex-class.md)   
 [Classe de CW2WEX](../../atl/reference/cw2wex-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
