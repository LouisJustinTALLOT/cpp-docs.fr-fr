---
title: Classe de CComGITPtr | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComGITPtr
- ATLBASE/ATL::CComGITPtr
- ATLBASE/ATL::CComGITPtr::CComGITPtr
- ATLBASE/ATL::CComGITPtr::Attach
- ATLBASE/ATL::CComGITPtr::CopyTo
- ATLBASE/ATL::CComGITPtr::Detach
- ATLBASE/ATL::CComGITPtr::GetCookie
- ATLBASE/ATL::CComGITPtr::Revoke
- ATLBASE/ATL::CComGITPtr::m_dwCookie
dev_langs:
- C++
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 049873ce6ff630e8f00ea5ad5ec9b3786bd5e71b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363624"
---
# <a name="ccomgitptr-class"></a>Classe de CComGITPtr
Cette classe fournit des méthodes pour traiter les pointeurs d’interface et le tableau global d’interface (GIT).  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class CComGITPtr
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type du pointeur d’interface à stocker dans le GIT.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComGITPtr::CComGITPtr](#ccomgitptr)|Constructeur.|  
|[CComGITPtr :: ~ CComGITPtr](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComGITPtr::Attach](#attach)|Appelez cette méthode pour inscrire le pointeur d’interface dans le tableau global d’interface (GIT).|  
|[CComGITPtr::CopyTo](#copyto)|Appelez cette méthode pour copier l’interface à partir de la table d’interface globale (GIT) pour le pointeur passé.|  
|[CComGITPtr::Detach](#detach)|Appelez cette méthode pour dissocier l’interface à partir de la `CComGITPtr` objet.|  
|[CComGITPtr::GetCookie](#getcookie)|Appelez cette méthode pour retourner le cookie à partir de la `CComGITPtr` objet.|  
|[CComGITPtr::Revoke](#revoke)|Appelez cette méthode pour supprimer l’interface de la table d’interface globale (GIT).|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComGITPtr::operator DWORD](#operator_dword)|Retourne le cookie à partir de la `CComGITPtr` objet.|  
|[CComGITPtr::operator =](#operator_eq)|Opérateur d'assignation.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Le cookie.|  
  
## <a name="remarks"></a>Notes  
 Les objets qui agrègent FTM et qui doivent utiliser des pointeurs d’interface obtenus à partir d’autres objets doivent suivre des étapes supplémentaires pour garantir que les interfaces sont correctement marshalés. En général, cela implique de stocker les pointeurs d’interface dans le GIT et l’obtention du pointeur de la GIT chaque fois qu’il est utilisé. La classe `CComGITPtr` est fourni pour vous aider à utiliser des pointeurs d’interface stockés dans le GIT.  
  
> [!NOTE]
>  La fonctionnalité de tableau global d’interface est uniquement disponible sur Windows 95 avec DCOM version 1.1 et ultérieure, Windows 98, Windows NT 4.0 avec Service Pack 3 et versions ultérieures et Windows 2000.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlbase.h  
  
##  <a name="attach"></a>  CComGITPtr::Attach  
 Appelez cette méthode pour inscrire le pointeur d’interface dans le tableau global d’interface (GIT).  
  
```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `p`  
 Le pointeur d’interface à ajouter à la GIT.  
  
 `dwCookie`  
 Le cookie est utilisé pour identifier le pointeur d’interface.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Dans les versions debug, une erreur d’assertion se produit si le GIT n’est pas valide, ou si le cookie est égal à NULL.  
  
##  <a name="ccomgitptr"></a>  CComGITPtr::CComGITPtr  
 Constructeur.  
  
```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `p`  
 Un pointeur d’interface à stocker dans le tableau global d’interface (GIT).  
  
 [in] `git`  
 Une référence à un fichier `CComGITPtr` objet.  
  
 [in] `dwCookie`  
 Un cookie est utilisé pour identifier le pointeur d’interface.  
  
 [in] `rv`  
 La source `CComGITPtr` pour déplacer des données d’objet.  
  
### <a name="remarks"></a>Notes  
 Crée un nouveau `CComGITPtr` de l’objet, en utilisant un existant `CComGITPtr` objet.  
  
 L’utilisation du constructeur `rv` est un constructeur de déplacement. Les données sont déplacées de la source, `rv`, puis `rv` est désactivée.  
  
##  <a name="dtor"></a>  CComGITPtr :: ~ CComGITPtr  
 Destructeur.  
  
```
~CComGITPtr() throw();
```  
  
### <a name="remarks"></a>Notes  
 Supprime l’interface à partir de la table d’interface globale (GIT), à l’aide de [CComGITPtr::Revoke](#revoke).  
  
##  <a name="copyto"></a>  CComGITPtr::CopyTo  
 Appelez cette méthode pour copier l’interface à partir de la table d’interface globale (GIT) pour le pointeur passé.  
  
```
HRESULT CopyTo(T** pp) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pp`  
 Le pointeur qui doit recevoir l’interface.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 L’interface de le GIT est copié vers le pointeur passé. Le pointeur doit être libéré par l’appelant quand il n’est plus nécessaire.  
  
##  <a name="detach"></a>  CComGITPtr::Detach  
 Appelez cette méthode pour dissocier l’interface à partir de la `CComGITPtr` objet.  
  
```
DWORD Detach() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le cookie à partir de la `CComGITPtr` objet.  
  
### <a name="remarks"></a>Notes  
 C’est à l’appelant de supprimer l’interface de le GIT, à l’aide de [CComGITPtr::Revoke](#revoke).  
  
##  <a name="getcookie"></a>  CComGITPtr::GetCookie  
 Appelez cette méthode pour retourner le cookie à partir de la `CComGITPtr` objet.  
  
```
DWORD GetCookie() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le cookie.  
  
### <a name="remarks"></a>Notes  
 Le cookie est une variable utilisée pour identifier une interface et son emplacement.  
  
##  <a name="m_dwcookie"></a>  CComGITPtr::m_dwCookie  
 Le cookie.  
  
```
DWORD m_dwCookie;
```  
  
### <a name="remarks"></a>Notes  
 Le cookie est une variable de membre utilisée pour identifier une interface et son emplacement.  
  
##  <a name="operator_eq"></a>  CComGITPtr::operator =  
 L’opérateur d’assignation.  
  
```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `p`  
 Pointeur vers une interface.  
  
 [in] `git`  
 Référence à un objet `CComGITPtr`.  
  
 [in] `dwCookie`  
 Un cookie est utilisé pour identifier le pointeur d’interface.  
  
 [in] `rv`  
 Le `CComGITPtr` pour déplacer des données à partir de.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la mise à jour `CComGITPtr` objet.  
  
### <a name="remarks"></a>Notes  
 Affecte une nouvelle valeur à un `CComGITPtr` objet, à partir d’un objet existant ou à partir d’une référence à un tableau global d’interface.  
  
##  <a name="operator_dword"></a>  CComGITPtr::operator DWORD  
 Retourne le cookie associé à le `CComGITPtr` objet.  
  
```  
operator DWORD() const;
```  
  
### <a name="remarks"></a>Notes  
 Le cookie est une variable utilisée pour identifier une interface et son emplacement.  
  
##  <a name="revoke"></a>  CComGITPtr::Revoke  
 Appelez cette méthode pour supprimer l’interface actuelle à partir de la table d’interface globale (GIT).  
  
```
HRESULT Revoke() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Supprime l’interface de le GIT.  
  
## <a name="see-also"></a>Voir aussi  
 [Marshaleur libre](../../atl/atl-and-the-free-threaded-marshaler.md)   
 [L’accès à des Interfaces entre les cloisonnements](http://msdn.microsoft.com/library/windows/desktop/ms682353)   
 [Quand utiliser le tableau Global d’Interface](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
