---
title: CGopherFile, classe | Microsoft Docs
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
ms.openlocfilehash: c6c4f87ffb1538e581320e9d6f36e8d4fbc6fc12
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335680"
---
# <a name="cgopherfile-class"></a>CGopherFile (classe)
Fournit les fonctionnalités permettant de rechercher et de lire des fichiers sur un serveur Gopher.  
  
> [!NOTE]
>  Les classes `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` et leurs membres ont été déconseillées, car ils ne fonctionnent pas sur la plate-forme Windows XP, mais ils continueront à fonctionner sur des plateformes antérieures.  
  
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
 Le service gopher n’autorise pas les utilisateurs à écrire des données dans un fichier gopher, car ce service fonctionne principalement comme une interface à menus pour trouver des informations. Le `CGopherFile` fonctions membres `Write`, `WriteString`, et `Flush` ne sont pas implémentées pour `CGopherFile`. Appel de ces fonctions sur un `CGopherFile` de l’objet, retourne un [exception CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Pour en savoir plus sur la façon `CGopherFile` fonctionne avec les autres classes Internet de MFC, consultez l’article [Internet programmation avec WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CGopherFile`  
  
## <a name="requirements"></a>Configuration requise  
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
 *hFile*  
 Handle vers un fichier HINTERNET.  
  
 *refLocator*  
 Une référence à un [objet CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objet.  
  
 *pConnection*  
 Un pointeur vers un [objet CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objet.  
  
 *hSession*  
 Handle vers la session Internet actuel.  
  
 *pstrLocator*  
 Un pointeur vers une chaîne utilisée pour rechercher le serveur gopher. Consultez [Gopher Sessions](cgopherlocator-class.md) pour plus d’informations sur les localisateurs gopher.  
  
 *dwLocLen*  
 Une valeur DWORD qui contient le nombre d’octets dans *pstrLocator*.  
  
 *dwContext*  
 Pointeur vers l’identificateur de contexte du fichier en cours d’ouverture.  
  
### <a name="remarks"></a>Notes  
 Vous devez un `CGopherFile` objet à lire à partir d’un fichier pendant une session d’Internet gopher.  
  
 Vous ne créez jamais un `CGopherFile` directement l’objet. Au lieu de cela, appelez [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) pour ouvrir un fichier sur un serveur gopher.  
  
## <a name="see-also"></a>Voir aussi  
 [CInternetFile, classe](../../mfc/reference/cinternetfile-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CInternetFile, classe](../../mfc/reference/cinternetfile-class.md)   
 [CGopherLocator, classe](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFileFind, classe](../../mfc/reference/cgopherfilefind-class.md)   
 [CGopherConnection, classe](../../mfc/reference/cgopherconnection-class.md)
