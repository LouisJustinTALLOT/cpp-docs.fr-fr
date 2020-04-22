---
title: CSharedFile, classe
ms.date: 11/04/2016
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
ms.openlocfilehash: c715ca1b8a2b647f89ada008f3c6606ca5e58783
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750390"
---
# <a name="csharedfile-class"></a>CSharedFile, classe

La classe [dérivée de CMemFile](../../mfc/reference/cmemfile-class.md)qui prend en charge les fichiers mémoire partagés.

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
|[CSharedFile::Detach](#detach)|Ferme le fichier mémoire partagé et renvoie la poignée de son bloc de mémoire.|
|[CSharedFile::SetHandle](#sethandle)|Attache le fichier mémoire partagé à un bloc mémoire.|

## <a name="remarks"></a>Notes

Les fichiers mémoire se comportent comme des fichiers disque. La différence est, un fichier mémoire est stocké dans la RAM plutôt que sur le disque. Un fichier mémoire est utile pour le stockage temporaire rapide, ou pour le transfert d’octets bruts ou d’objets sérialisés entre des processus indépendants.

Les fichiers mémoire partagés diffèrent des autres fichiers mémoire dans cette mémoire pour eux est allouée avec la fonction [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows. La `CSharedFile` classe stocke les données dans un `GlobalAlloc`bloc de mémoire mondial attribué (créé à l’aide), et ce bloc de mémoire `IDataObject`peut être partagé à l’aide de DDE, le Clipboard, ou d’autres opérations de transfert de données uniformes OLE /COM, par exemple, en utilisant .

`GlobalAlloc`retourne une poignée HGLOBAL plutôt qu’un pointeur à la mémoire, comme le pointeur retourné par [malloc](../../c-runtime-library/reference/malloc.md). La poignée HGLOBAL est nécessaire dans certaines applications. Par exemple, pour mettre des données sur le Clipboard, vous avez besoin d’une poignée HGLOBAL.

`CSharedFile`n’utilise pas de fichiers cartographiés par la mémoire, et les données ne peuvent pas être directement partagées entre les processus.

`CSharedFile`les objets peuvent automatiquement allouer leur propre mémoire. Ou, vous pouvez attacher votre `CSharedFile` propre bloc de mémoire à l’objet en appelant [CSharedFile::SetHandle](#sethandle). Dans les deux cas, la mémoire pour `nGrowBytes`la culture du fichier `nGrowBytes` mémoire est automatiquement allouée par incréments de taille si elle n’est pas nulle.

Pour plus d’informations, consultez l’article [Fichiers dans MFC](../../mfc/files-in-mfc.md) et [Traitement des fichiers](../../c-runtime-library/file-handling.md) dans la référence de la bibliothèque *Run-Time*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>Spécifications

**En-tête:** afxadv.h

## <a name="csharedfilecsharedfile"></a><a name="csharedfile"></a>CSharedFile::CSharedFile

Construit un `CSharedFile` objet et alloue la mémoire pour lui.

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>Paramètres

*nAllocFlags*<br/>
Drapeaux indiquant comment la mémoire doit être allouée. Consultez [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) pour une liste de valeurs de drapeau valides.

*nGrowBytes (en)*<br/>
L’augmentation de l’allocation de mémoire dans les octets.

## <a name="csharedfiledetach"></a><a name="detach"></a>CSharedFile::Detach

Appelez cette fonction pour fermer le fichier mémoire et le détacher du bloc de mémoire.

```
HGLOBAL Detach();
```

### <a name="return-value"></a>Valeur de retour

La poignée du bloc mémoire qui contient le contenu du fichier mémoire.

### <a name="remarks"></a>Notes

Vous pouvez le rouvrir en appelant [SetHandle](#sethandle), en utilisant la poignée retournée par **Detach**.

## <a name="csharedfilesethandle"></a><a name="sethandle"></a>CSharedFile::SetHandle

Appelez cette fonction pour attacher un `CSharedFile` bloc de mémoire globale à l’objet.

```cpp
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>Paramètres

*hGlobalMemory (en)*<br/>
Gérer à la mémoire globale `CSharedFile`d’être attaché à la .

*bAllowGrow (en)*<br/>
Précise si le bloc de mémoire est autorisé à se développer.

### <a name="remarks"></a>Notes

Si *bAllowGrow* n’est paszero, la taille du bloc de mémoire est augmentée au besoin, par exemple, si vous essayez d’écrire plus d’octets au fichier que la taille du bloc de mémoire.

## <a name="see-also"></a>Voir aussi

[Classe CMemFile](../../mfc/reference/cmemfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CMemFile](../../mfc/reference/cmemfile-class.md)
