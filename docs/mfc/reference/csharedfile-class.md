---
title: Classe CSharedFile | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
dev_langs:
- C++
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bee22940fb197d480f4ae3550d8dd59780c256b5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370179"
---
# <a name="csharedfile-class"></a>Classe CSharedFile
Le [CMemFile](../../mfc/reference/cmemfile-class.md)-classe dérivée qui prend en charge de fichiers de mémoire partagé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSharedFile : public CMemFile  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSharedFile::CSharedFile](#csharedfile)|Construit un objet `CSharedFile`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CSharedFile::Detach](#detach)|Ferme le fichier de mémoire partagée et retourne le handle de son bloc de mémoire.|  
|[CSharedFile::SetHandle](#sethandle)|Joint le fichier de mémoire partagée à un bloc de mémoire.|  
  
## <a name="remarks"></a>Notes  
 Fichiers de mémoire se comportent comme les fichiers de disque, sauf que le fichier est stocké dans la mémoire RAM, plutôt que sur le disque. Un fichier de mémoire est utile pour le stockage temporaire rapide ou le transfert d’octets bruts ou objets sérialisés entre des processus indépendants.  
  
 Les fichiers de mémoire partagée diffèrent des autres fichiers de mémoire que mémoire leur est allouée avec le [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) fonction Windows. Le `CSharedFile` classe stocke les données dans un bloc de mémoire alloués globalement (créé à l’aide de **GlobalAlloc**), et ce bloc de mémoire peut être partagé à l’aide de DDE, le Presse-papiers ou autres opérations de transfert OLE/COM de données uniforme, par exemple, à l’aide de `IDataObject`.  
  
 **GlobalAlloc** retourne un `HGLOBAL` gérer au lieu d’un pointeur vers la mémoire, telles que le pointeur retourné par [malloc](../../c-runtime-library/reference/malloc.md). Le `HGLOBAL` handle n’est nécessaire dans certaines applications. Par exemple, pour placer des données le Presse-papiers vous devez un `HGLOBAL` gérer.  
  
 Notez que `CSharedFile` ne pas les utiliser mappé en mémoire et les données ne peut pas être partagées directement entre les processus.  
  
 `CSharedFile` objets peuvent allouer automatiquement leur propre mémoire, ou vous pouvez attacher votre propre bloc de mémoire à la `CSharedFile` objet en appelant [CSharedFile::SetHandle](#sethandle). Dans les deux cas, la mémoire pour la croissance d’automatiquement le fichier de mémoire est allouée dans `nGrowBytes`-taille par incréments si `nGrowBytes` n’est pas zéro.  
  
 Pour plus d’informations, consultez l’article [fichiers dans MFC](../../mfc/files-in-mfc.md) et [gestion des fichiers](../../c-runtime-library/file-handling.md) dans les *Run-Time Library Reference*.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CMemFile](../../mfc/reference/cmemfile-class.md)  
  
 `CSharedFile`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxadv.h  
  
##  <a name="csharedfile"></a>  CSharedFile::CSharedFile  
 Construit un `CSharedFile` de l’objet et alloue de la mémoire pour celle-ci.  
  
```  
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,  
    UINT nGrowBytes = 4096);
```  
  
### <a name="parameters"></a>Paramètres  
 *nAllocFlags*  
 Indicateurs indiquant comment la mémoire doit être allouée. Consultez [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) pour obtenir la liste de valeurs d’indicateur valide.  
  
 `nGrowBytes`  
 L’incrément de l’allocation de mémoire en octets.  
  
##  <a name="detach"></a>  CSharedFile::Detach  
 Appelez cette fonction pour fermer le fichier de mémoire et de le détacher le bloc de mémoire.  
  
```  
HGLOBAL Detach();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle du bloc de mémoire qui contient le contenu du fichier en mémoire.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez le rouvrir en appelant [SetHandle](#sethandle), à l’aide du handle retourné par **détachement**.  
  
##  <a name="sethandle"></a>  CSharedFile::SetHandle  
 Appelez cette fonction pour attacher un bloc de mémoire globale pour la `CSharedFile` objet.  
  
```  
void SetHandle(
    HGLOBAL hGlobalMemory,  
    BOOL bAllowGrow = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *hGlobalMemory*  
 Handle vers la mémoire globale à joindre à la `CSharedFile`.  
  
 `bAllowGrow`  
 Spécifie si le bloc de mémoire est autorisé à croître.  
  
### <a name="remarks"></a>Notes  
 Si `bAllowGrow` est différent de zéro, la taille du bloc de mémoire est augmentée si nécessaire, par exemple, si une tentative est effectuée pour écrire des octets dans le fichier que vous ont été alloués pour le bloc de mémoire.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe CMemFile](../../mfc/reference/cmemfile-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CMemFile, classe](../../mfc/reference/cmemfile-class.md)
