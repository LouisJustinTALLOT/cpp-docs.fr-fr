---
title: CGopherFile (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
dev_langs:
- C++
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98fa4b2a489b8abb3951719dc74e618a054a4025
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366881"
---
# <a name="cgopherfile-class"></a>CGopherFile (classe)
Fournit les fonctionnalités permettant de rechercher et de lire des fichiers sur un serveur Gopher.  
  
> [!NOTE]
>  Les classes `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` et leurs membres ont été déconseillées, car ils ne fonctionnent pas sur la plateforme Windows XP, mais ils continuent de fonctionner sur des plateformes antérieures.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CGopherFile : public CInternetFile  
```  
  
## <a name="members"></a>Membres  
  
### <a name="protected-constructors"></a>Constructeurs protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[CGopherFile::CGopherFile](#cgopherfile)|Construit un objet `CGopherFile`.|  
  
## <a name="remarks"></a>Notes  
 Le service gopher n’autorise pas les utilisateurs à écrire des données dans un fichier gopher, car ce service fonctionne principalement comme une interface de menus pour la recherche d’informations. Le `CGopherFile` fonctions membres **écrire**, `WriteString`, et `Flush` ne sont pas implémentées pour `CGopherFile`. Appel de ces fonctions sur un `CGopherFile` de l’objet, retourne un [exception CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Pour en savoir plus sur la façon `CGopherFile` fonctionne avec les autres classes MFC Internet, consultez l’article [de programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CGopherFile`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxinet.h  
  
##  <a name="cgopherfile"></a>  CGopherFile::CGopherFile  
 Cette fonction membre est appelée pour construire un `CGopherFile` objet.  
  
```  
CGopherFile(
    HINTERNET hFile,  
    CGopherLocator& refLocator,  
    CGopherConnection* pConnection);

 
CGopherFile(
    HINTERNET hFile,  
    HINTERNET hSession,  
    LPCTSTR pstrLocator,  
    DWORD dwLocLen,  
    DWORD_PTR dwContext);
```  
  
### <a name="parameters"></a>Paramètres  
 `hFile`  
 Un handle vers un `HINTERNET` fichier.  
  
 `refLocator`  
 Une référence à un [objet CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objet.  
  
 `pConnection`  
 Un pointeur vers un [objet CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objet.  
  
 `hSession`  
 Handle vers la session Internet en cours.  
  
 `pstrLocator`  
 Un pointeur vers une chaîne utilisée pour rechercher le serveur gopher. Consultez [Gopher Sessions](cgopherlocator-class.md) pour plus d’informations sur les localisateurs gopher.  
  
 *dwLocLen*  
 Une valeur DWORD qui contient le nombre d’octets dans `pstrLocator`.  
  
 `dwContext`  
 Pointeur vers l’identificateur de contexte du fichier en cours d’ouverture.  
  
### <a name="remarks"></a>Notes  
 Vous avez besoin une `CGopherFile` objet à lire à partir d’un fichier pendant une session d’Internet gopher.  
  
 Vous ne créez jamais un `CGopherFile` directement l’objet. Au lieu de cela, appelez [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) pour ouvrir un fichier sur un serveur gopher.  
  
## <a name="see-also"></a>Voir aussi  
 [CInternetFile (classe)](../../mfc/reference/cinternetfile-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CInternetFile (classe)](../../mfc/reference/cinternetfile-class.md)   
 [Classe d’objet CGopherLocator](../../mfc/reference/cgopherlocator-class.md)   
 [Classe de CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)   
 [CGopherConnection, classe](../../mfc/reference/cgopherconnection-class.md)
