---
title: CSharedFile, classe | Microsoft Docs
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
ms.openlocfilehash: 38267ed5755b99bd97e4c923611d297673fcc41e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215581"
---
# <a name="csharedfile-class"></a>CSharedFile, classe
Le [CMemFile](../../mfc/reference/cmemfile-class.md)-classe dérivée qui prend en charge les fichiers de la mémoire partagée.  
  
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
 Fichiers de mémoire se comportent comme les fichiers de disque, à ceci près que le fichier est stocké dans la mémoire RAM, plutôt que sur le disque. Un fichier de mémoire est utile pour un stockage temporaire rapide ou pour transférer les octets bruts ou objets sérialisés entre processus indépendants.  
  
 Les fichiers de mémoire partagée la différence des autres fichiers de mémoire mémoire leur est allouée à la [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) (fonction) Windows. Le `CSharedFile` classe stocke les données dans un bloc de mémoire alloué dans le monde entier (créé à l’aide `GlobalAlloc`), et ce bloc de mémoire peut être partagé à l’aide de DDE, le Presse-papiers ou autres opérations de transfert OLE/COM de données uniforme, par exemple, à l’aide de `IDataObject`.  
  
 `GlobalAlloc` Retourne un HGLOBAL gérer au lieu d’un pointeur vers la mémoire, telles que le pointeur retourné par [malloc](../../c-runtime-library/reference/malloc.md). Le descripteur HGLOBAL est nécessaire dans certaines applications. Par exemple, pour placer des données dans le Presse-papiers, vous devez descripteur HGLOBAL.  
  
 Veuillez noter que `CSharedFile` ne pas les fichiers d’utilisation mappé en mémoire et les données ne peuvent pas être partagées directement entre les processus.  
  
 `CSharedFile` objets peuvent allouer automatiquement leur propre mémoire, ou vous pouvez attacher votre propre bloc de mémoire à la `CSharedFile` objet en appelant [CSharedFile::SetHandle](#sethandle). Dans les deux cas, la mémoire pour la croissance d’automatiquement le fichier de la mémoire est allouée dans `nGrowBytes`-taille par incréments si `nGrowBytes` n’est pas égal à zéro.  
  
 Pour plus d’informations, consultez l’article [fichiers dans MFC](../../mfc/files-in-mfc.md) et [gestion des fichiers](../../c-runtime-library/file-handling.md) dans le *Run-Time Library Reference*.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CMemFile](../../mfc/reference/cmemfile-class.md)  
  
 `CSharedFile`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxadv.h  
  
##  <a name="csharedfile"></a>  CSharedFile::CSharedFile  
 Construit un `CSharedFile` de l’objet et alloue la mémoire pour elle.  
  
```  
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,  
    UINT nGrowBytes = 4096);
```  
  
### <a name="parameters"></a>Paramètres  
 *nAllocFlags*  
 Indicateurs indiquant comment la mémoire doit être allouée. Consultez [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) pour obtenir la liste de valeurs d’indicateur valide.  
  
 *nGrowBytes*  
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
  
 *bAllowGrow*  
 Spécifie si le bloc de mémoire est autorisé à croître.  
  
### <a name="remarks"></a>Notes  
 Si *bAllowGrow* est différent de zéro, la taille du bloc de mémoire est augmentée en fonction des besoins, par exemple, si une tentative est effectuée pour écrire des octets dans le fichier qu’ont été alloués pour le bloc de mémoire.  
  
## <a name="see-also"></a>Voir aussi  
 [CMemFile, classe](../../mfc/reference/cmemfile-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CMemFile, classe](../../mfc/reference/cmemfile-class.md)
