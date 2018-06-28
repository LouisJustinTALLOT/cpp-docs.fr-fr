---
title: Classe d’objet CGopherLocator | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGopherLocator
- AFXINET/CGopherLocator
- AFXINET/CGopherLocator::CGopherLocator
- AFXINET/CGopherLocator::GetLocatorType
dev_langs:
- C++
helpviewer_keywords:
- CGopherLocator [MFC], CGopherLocator
- CGopherLocator [MFC], GetLocatorType
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f466864e694f332f70d9f5932a528917a000974
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041284"
---
# <a name="cgopherlocator-class"></a>Classe d’objet CGopherLocator
Obtient un « localisateur » d’un serveur gopher, détermine le type du localisateur et rend le localisateur accessible à [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md).  
  
> [!NOTE]
>  Les classes `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` et leurs membres ont été déconseillées, car ils ne fonctionnent pas sur la plateforme Windows XP, mais ils continuent de fonctionner sur des plateformes antérieures.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CGopherLocator : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CGopherLocator::CGopherLocator](#cgopherlocator)|Construit un objet `CGopherLocator`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CGopherLocator::GetLocatorType](#getlocatortype)|Analyse un localisateur gopher et détermine ses attributs.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CGopherLocator::operator LPCTSTR](#operator_lpctstr)|Accède directement aux caractères stockés dans un `CGopherLocator` objet comme une chaîne de style C.|  
  
## <a name="remarks"></a>Notes  
 Une application doit obtenir les recherche d’un serveur gopher avant d’extraire des informations à partir de ce serveur. Une fois qu’il a le localisateur, il doit traiter le localisateur comme un jeton opaque.  
  
 Chaque adresse gopher possède des attributs qui déterminent le type de fichier ou le serveur a été trouvé. Consultez [GetLocatorType](#getlocatortype) pour obtenir la liste des types de localisateurs de gopher.  
  
 Une application utilise normalement le localisateur pour les appels à [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) pour récupérer une information spécifique.  
  
 Pour en savoir plus sur la façon `CGopherLocator` fonctionne avec les autres classes MFC Internet, consultez l’article [de programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGopherLocator`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxinet.h  
  
##  <a name="cgopherlocator"></a>  CGopherLocator::CGopherLocator  
 Cette fonction membre est appelée pour créer un `CGopherLocator` objet.  
  
```  
CGopherLocator(const CGopherLocator& ref);
```  
  
### <a name="parameters"></a>Paramètres  
 *ref*  
 Une référence à une constante `CGopherLocator` objet.  
  
### <a name="remarks"></a>Notes  
 Vous ne créez jamais un `CGopherLocator` directement l’objet. Au lieu de cela, appelez [CGopherConnection::CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) pour créer et retourner un pointeur vers le `CGopherLocator` objet.  
  
##  <a name="getlocatortype"></a>  CGopherLocator::GetLocatorType  
 Appelez cette fonction membre pour obtenir le type de recherche.  
  
```  
BOOL GetLocatorType(DWORD& dwRef) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *dwRef*  
 Une référence à un `DWORD` qui recevront le type de localisateur. Consultez **remarques** pour un tableau de types de recherche.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelé pour déterminer la cause de l’erreur.  
  
### <a name="remarks"></a>Notes  
 Les types possibles sont les suivantes :  
  
|Value|Signification|  
|-----------|-------------|  
|GOPHER_TYPE_TEXT_FILE|Fichier texte ASCII.|  
|GOPHER_TYPE_DIRECTORY|Un répertoire d’autres éléments Gopher.|  
|GOPHER_TYPE_CSO|Un serveur d’annuaire téléphonique responsable de la sécurité.|  
|GOPHER_TYPE_ERROR|Indique une condition d’erreur.|  
|GOPHER_TYPE_MAC_BINHEX|Un fichier Macintosh format BINHEX.|  
|GOPHER_TYPE_DOS_ARCHIVE|Un fichier d’archive déni de service.|  
|GOPHER_TYPE_UNIX_UUENCODED|Un fichier UUEncode.|  
|GOPHER_TYPE_INDEX_SERVER|Un serveur d’index.|  
|GOPHER_TYPE_TELNET|Un serveur Telnet.|  
|GOPHER_TYPE_BINARY|Un fichier binaire.|  
|GOPHER_TYPE_REDUNDANT|Un serveur en double. Les informations contenues dans sont un doublon du serveur principal. Le serveur principal est la dernière entrée de répertoire qui n’avait pas d’un type GOPHER_TYPE_REDUNDANT.|  
|GOPHER_TYPE_TN3270|Un serveur TN3270.|  
|GOPHER_TYPE_GIF|Un fichier de graphique GIF.|  
|GOPHER_TYPE_IMAGE|Un fichier image.|  
|GOPHER_TYPE_BITMAP|Un fichier bitmap.|  
|GOPHER_TYPE_MOVIE|Un fichier vidéo.|  
|GOPHER_TYPE_SOUND|Un fichier audio.|  
|GOPHER_TYPE_HTML|Document HTML.|  
|GOPHER_TYPE_PDF|Un fichier PDF.|  
|GOPHER_TYPE_CALENDAR|Un fichier de calendrier.|  
|GOPHER_TYPE_INLINE|Un fichier inline.|  
|GOPHER_TYPE_UNKNOWN|Le type d’élément est inconnu.|  
|GOPHER_TYPE_ASK|Demandez à + élément.|  
|GOPHER_TYPE_GOPHER_PLUS|Un élément Gopher +.|  
  
##  <a name="operator_lpctstr"></a>  CGopherLocator::operator LPCTSTR  
 Cet opérateur de conversion utile fournit une méthode efficace pour accéder à la chaîne C se terminant par null contenue dans un `CGopherLocator` objet.  
  
```  
operator LPCTSTR () const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur de caractère pour les données de la chaîne.  
  
### <a name="remarks"></a>Notes  
 Aucuns caractères ne sont copiés ; seul un pointeur est retourné.  
  
## <a name="see-also"></a>Voir aussi  
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind, classe](../../mfc/reference/cgopherfilefind-class.md)
