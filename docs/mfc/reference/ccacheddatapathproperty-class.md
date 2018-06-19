---
title: Classe de CCachedDataPathProperty | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
dev_langs:
- C++
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29e46f7e65d6c2f9b5c0d29007cd31f660754957
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355458"
---
# <a name="ccacheddatapathproperty-class"></a>Classe de CCachedDataPathProperty
Implémente une propriété de contrôle OLE transférée de façon asynchrone et mise en cache dans un fichier de mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CCachedDataPathProperty : public CDataPathProperty  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|Construit un objet `CCachedDataPathProperty`.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile` objet dans lequel en cache des données.|  
  
## <a name="remarks"></a>Notes  
 Un fichier de mémoire est stocké dans la mémoire RAM, plutôt que sur le disque et est utile pour les transferts d’accélérée temporaires.  
  
 Avec **CAysncMonikerFile** et `CDataPathProperty`, `CCachedDataPathProperty` fournit les fonctionnalités pour l’utilisation de monikers asynchrones dans les contrôles OLE. Avec `CCachedDataPathProperty` des objets, vous êtes en mesure de transférer des données de façon asynchrone à partir d’une source de l’URL ou le fichier et le stocker dans un fichier de mémoire via le `m_Cache` variable publique. Toutes les données sont stockées dans le fichier de mémoire, et il n’est pas nécessaire de substituer [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) sauf si vous souhaitez surveiller les notifications et y répondre. Par exemple, si vous transférez une grande taille. Fichier GIF et que vous souhaitez notifier votre contrôle que davantage de données est arrivé et qu’il doit se redessiner, substituez `OnDataAvailable` pour rendre la notification.  
  
 La classe `CCachedDataPathProperty` est dérivée de `CDataPathProperty`.  
  
 Pour plus d’informations sur l’utilisation de monikers asynchrones et les contrôles ActiveX dans les applications Internet, consultez les rubriques suivantes :  
  
- [Internet premières étapes : Les contrôles ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
- [Internet premières étapes : Les Monikers asynchrones](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)  
  
 `CCachedDataPathProperty`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxctl.h  
  
##  <a name="ccacheddatapathproperty"></a>  CCachedDataPathProperty::CCachedDataPathProperty  
 Construit un objet `CCachedDataPathProperty`.  
  
```  
CCachedDataPathProperty(COleControl* pControl = NULL);

 
CCachedDataPathProperty(
    LPCTSTR lpszPath,  
    COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `pControl`  
 Un pointeur vers l’objet de contrôle ActiveX à associer à ce `CCachedDataPathProperty` objet.  
  
 `lpszPath`  
 Le chemin d’accès, qui peut être absolu ou relatif, utilisé pour créer un moniker asynchrone qui fait référence à l’emplacement absolu réel de la propriété. `CCachedDataPathProperty` utilise des URL, pas les noms de fichiers. Si vous souhaitez un `CCachedDataPathProperty` de l’objet d’un fichier, faites précéder file:// pour le chemin d’accès.  
  
### <a name="remarks"></a>Notes  
 Le `COleControl` objet pointé par `pControl` est utilisé par [ouvrir](../../mfc/reference/cdatapathproperty-class.md#open) et récupérés par les classes dérivées. Si `pControl` est **NULL**, le contrôle utilisé avec **ouvrir** doit être défini avec [SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol). Si `lpszPath` est **NULL**, vous pouvez passer dans le chemin d’accès via **ouvrir** ou définissez-la avec [SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath).  
  
##  <a name="m_cache"></a>  CCachedDataPathProperty::m_Cache  
 Contient le nom de classe du fichier de mémoire dans lequel les données sont mises en cache.  
  
```  
CMemFile m_Cache;  
```  
  
### <a name="remarks"></a>Notes  
 Un fichier de mémoire est stocké dans la mémoire RAM, plutôt que sur le disque.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CDataPathProperty, classe](../../mfc/reference/cdatapathproperty-class.md)
