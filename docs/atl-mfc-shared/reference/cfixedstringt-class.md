---
title: CFixedStringT (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
dev_langs:
- C++
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93125d15be32a95d71c763f476fad700dab65a3b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356985"
---
# <a name="cfixedstringt-class"></a>CFixedStringT (classe)
Cette classe représente un objet string avec une mémoire tampon de caractères fixe.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```  
  
#### <a name="parameters"></a>Paramètres  
 `StringType`  
 Utilisé comme classe de base pour l’objet de chaîne fixe et peut être tout `CStringT`-type de base. Voici quelques exemples `CString`, `CStringA`, et `CStringW`.  
  
 *t_nChars*  
 Le nombre de caractères stockés dans la mémoire tampon.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CFixedStringT::CFixedStringT](#cfixedstringt)|Le constructeur de l’objet string.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CFixedStringT::operator =](#eq)|Affecte une nouvelle valeur à un `CFixedStringT` objet.|  
  
## <a name="remarks"></a>Notes  
 Cette classe est un exemple d’une classe de chaîne personnalisée basée sur `CStringT`. Bien que très similaire, les deux classes sont différents dans l’implémentation. Principales différences entre `CFixedStringT` et `CStringT` sont :  
  
-   La mémoire tampon caractère initial est alloué dans le cadre de l’objet et taille *t_nChars*. Cela permet la **CFixedString** objet pour occuper un segment de mémoire contiguë pour des raisons de performances. Toutefois, si le contenu d’un `CFixedStringT` objet excède *t_nChars*, la mémoire tampon est allouée dynamiquement.  
  
-   La mémoire tampon de caractères pour un `CFixedStringT` objet est toujours la même longueur ( *t_nChars*). Il n’existe aucune limitation quant à la taille de mémoire tampon pour `CStringT` objets.  
  
-   Le Gestionnaire de mémoire pour `CFixedStringT` personnalisé tel que le partage d’un [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) objet entre deux ou plusieurs `CFixedStringT` objectsis ne pas autorisé. `CStringT` objets n’ont pas cette limitation.  
  
 Pour plus d’informations sur la personnalisation de `CFixedStringT` et gestion de la mémoire pour les objets string en général, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IAtlStringMgr`  
  
 `StringType`  
  
 `CFixedStringMgr`  
  
 `CFixedStringT`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** cstringt.h  
  
##  <a name="cfixedstringt"></a>  CFixedStringT::CFixedStringT  
 Construit un objet `CFixedStringT`.  
  
```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT(const StringType& str);
CFixedStringT(const StringType::XCHAR* psz);
explicit CFixedStringT(const StringType::YCHAR* psz);
explicit CFixedStringT(const unsigned char* psz);
```  
  
### <a name="parameters"></a>Paramètres  
 `psz`  
 Une chaîne se terminant par null à copier dans cette `CFixedStringT` objet.  
  
 `str`  
 Existant `CFixedStringT` objet doit être copié dans ce `CFixedStringT` objet.  
  
 `pStringMgr`  
 Un pointeur vers le Gestionnaire de mémoire de le `CFixedStringT` objet. Pour plus d’informations sur `IAtlStringMgr` et gestion de la mémoire pour `CFixedStringT`, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
### <a name="remarks"></a>Notes  
 Étant donné que les constructeurs copient les données d’entrée dans le nouveau stockage alloué, vous devez être conscient que la mémoire peuvent entraîner des exceptions. Notez que certaines de ces constructeurs agissent comme des fonctions de conversion.  
  
##  <a name="operator__eq"></a>  CFixedStringT::operator =  
 Réinitialise un existant `CFixedStringT` objet avec les nouvelles données.  
  
```
CFixedStringT<StringType, t_nChars>& operator=(
  const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT<StringType, t_nChars>& operator=(const char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* psz);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& str);
```  
  
### <a name="parameters"></a>Paramètres  
 `str`  
 Une chaîne se terminant par null à copier dans cette `CFixedStringT` objet.  
  
 `psz`  
 Existant `CFixedStringT` à copier dans cette `CFixedStringT` objet.  
  
### <a name="remarks"></a>Notes  
 Vous devez être conscient que les exceptions peuvent se produire lorsque vous utilisez l’opérateur d’assignation, car le nouveau stockage est souvent alloué pour contenir résultant de la mémoire `CFixedStringT` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [CStringT (classe)](../../atl-mfc-shared/reference/cstringt-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes de partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)




