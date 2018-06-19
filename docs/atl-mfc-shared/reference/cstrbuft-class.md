---
title: Classe de CStrBufT | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStrBufT
- ATLSIMPSTR/ATL::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::SetLength
- ATLSIMPSTR/ATL::CStrBufT::AUTO_LENGTH
- ATLSIMPSTR/ATL::CStrBufT::SET_LENGTH
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 695c3bc4c5e03f2ff6c1865f456b1ef358e3dcf4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361356"
---
# <a name="cstrbuft-class"></a>Classe de CStrBufT
Cette classe fournit le nettoyage automatique des ressources des `GetBuffer` et `ReleaseBuffer` appelle une `CStringT` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename TCharType>
class CStrBufT
```  
  
#### <a name="parameters"></a>Paramètres  
 *TCharType*  
 Le type de caractère de la `CStrBufT` classe. Il peut s'agir d'une des valeurs suivantes :  
  
- `char` (pour les chaînes de caractères ANSI)  
  
- `wchar_t` (pour les chaînes de caractères Unicode)  
  
- **TCHAR** (pour les chaînes de caractères ANSI et Unicode)  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`PCXSTR`|Pointeur vers une chaîne constante.|  
|`PXSTR`|Un pointeur vers une chaîne.|  
|`StringType`|Le type de chaîne dont la mémoire tampon doit être manipulées par les spécialisations de ce modèle de classe.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CStrBufT::CStrBufT](#cstrbuft)|Le constructeur de l’objet de mémoire tampon de chaîne.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CStrBufT::SetLength](#setlength)|Définit la longueur du tampon de caractères de l’objet de chaîne associées.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CStrBufT::operator PCXSTR](#operator_pcxstr)|Récupère un **const** pointeur vers la mémoire tampon de caractères de l’objet de chaîne associées.|  
|[CStrBufT::operator PXSTR](#operator_pxstr)|Récupère un pointeur vers la mémoire tampon de caractères de l’objet de chaîne associées.|  
  
### <a name="public-constants"></a>Constantes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[CStrBufT::AUTO_LENGTH](#auto_length)|Déterminer automatiquement la nouvelle longueur de la chaîne de version.|  
|[CStrBufT::SET_LENGTH](#set_length)|Définir la longueur de l’objet de chaîne au moment de GetBuffer|  
  
## <a name="remarks"></a>Notes  
 Cette classe est utilisée comme une classe wrapper pour le remplacement des appels à [GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) et [ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer), ou [GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) et `ReleaseBuffer`.  
  
 Principalement conçu comme une classe d’assistance, `CStrBufT` offre un moyen pratique pour un développeur de travailler avec la mémoire tampon de caractères d’un objet de chaîne sans se préoccuper de procédure ou quand il doit appeler `ReleaseBuffer`. Cela est possible, car l’objet de wrapper est hors de portée naturellement dans le cas d’une exception ou de plusieurs chemins de code existant ; à l’origine de son destructeur de libérer la ressource de chaîne.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlsimpstr.h  
  
##  <a name="auto_length"></a>  CStrBufT::AUTO_LENGTH  
 Déterminer automatiquement la nouvelle longueur de la chaîne de version.  
  
```
static const DWORD AUTO_LENGTH = 0x01;
```  
  
### <a name="remarks"></a>Notes  
 Déterminer automatiquement la nouvelle longueur de la chaîne de version. La chaîne doit être terminée par null.  
  
##  <a name="cstrbuft"></a>  CStrBufT::CStrBufT  
 Construit un objet de la mémoire tampon.  
  
```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `str`  
 L’objet de chaîne associé à la mémoire tampon. En règle générale, le développeur utilise les typedefs prédéfinis de **CStrBuf** ( **TCHAR** variante), **CStrBufA** ( `char` variante) et **CStrBufW**  ( `wchar_t` variante).  
  
 *nMinLength*  
 La longueur minimale de la mémoire tampon de caractères.  
  
 `dwFlags`  
 Détermine si la longueur de chaîne est déterminée automatiquement. Il peut s'agir d'une des valeurs suivantes :  
  
- **AUTO_LENGTH** longueur de chaîne est automatiquement déterminé lorsque [CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) est appelée. La chaîne doit être terminée par null. Valeur par défaut.  
  
- **SET_LENGTH** longueur de la chaîne est définie lorsque [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) est appelée.  
  
### <a name="remarks"></a>Notes  
 Crée un mémoire tampon de chaîne pour l’objet de chaîne associées. Pendant la construction, [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) ou [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) est appelée.  
  
 Notez que le constructeur de copie est `private`.  
  
##  <a name="operator_pcxstr"></a>  CStrBufT::operator PCXSTR  
 Accède directement aux caractères stockés dans l’objet de chaîne associées en une chaîne de style C.  
  
```  
operator PCXSTR() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur de caractère pour les données de la chaîne.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour retourner un pointeur vers la mémoire tampon de caractères d’un objet string. Impossible de modifier le contenu de l’objet string avec ce pointeur.  
  
##  <a name="operator_pxstr"></a>  CStrBufT::operator PXSTR  
 Accède directement aux caractères stockés dans l’objet de chaîne associées en une chaîne de style C.  
  
```
operator PXSTR() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur de caractère pour les données de la chaîne.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour retourner un pointeur vers la mémoire tampon de caractères d’un objet string. Le développeur peut modifier le contenu de l’objet string avec ce pointeur.  
  
##  <a name="pcxstr"></a>  CStrBufT::PCXSTR  
 Pointeur vers une chaîne constante.  
  
```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```  
  
##  <a name="pxstr"></a>  CStrBufT::PXSTR  
 Un pointeur vers une chaîne.  
  
```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```  
  
##  <a name="set_length"></a>  CStrBufT::SET_LENGTH  
 Définir la longueur de l’objet string à `GetBuffer` heure.  
  
```
static const DWORD SET_LENGTH = 0x02;
```  
  
### <a name="remarks"></a>Notes  
 Définissez la longueur de l’objet de chaîne au moment de GetBuffer.  
  
 Détermine si [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) et [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) sont appelées lors de la construction de l’objet de mémoire tampon de chaîne.  
  
##  <a name="setlength"></a>  CStrBufT::SetLength  
 Définit la longueur de la mémoire tampon de caractères.  
  
```
void SetLength(int nLength);
```  
  
### <a name="parameters"></a>Paramètres  
 `nLength`  
 Nouvelle longueur de la mémoire tampon de caractères de l’objet string.  
  
> [!NOTE]
>  Doit être inférieure ou égale à la longueur de la mémoire tampon minimale spécifiée dans le constructeur de `CStrBufT`.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour définir la longueur de la chaîne représentée par l’objet de la mémoire tampon.  
  
##  <a name="stringtype"></a>  CStrBufT::StringType  
 Le type de chaîne dont la mémoire tampon doit être manipulées par les spécialisations de ce modèle de classe.  
  
```
typedef CSimpleStringT<TCharType> StringType;
```  
  
### <a name="remarks"></a>Notes  
 **TCharType** est le type de caractère utilisé pour spécialiser le modèle de classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes de partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)


