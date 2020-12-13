---
description: 'En savoir plus sur : classe CSharedFile'
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
ms.openlocfilehash: 0eb2f76bdfa9e10c660f405e225698289b506014
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342829"
---
# <a name="csharedfile-class"></a>CSharedFile, classe

Classe dérivée de [CMemFile](../../mfc/reference/cmemfile-class.md)qui prend en charge les fichiers de mémoire partagée.

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
|[CSharedFile ::D Etach](#detach)|Ferme le fichier de mémoire partagée et retourne le handle de son bloc de mémoire.|
|[CSharedFile::SetHandle](#sethandle)|Joint le fichier de mémoire partagée à un bloc de mémoire.|

## <a name="remarks"></a>Notes

Les fichiers de mémoire se comportent comme des fichiers disque. La différence est qu’un fichier de mémoire est stocké dans la mémoire RAM plutôt que sur le disque. Un fichier de mémoire est utile pour le stockage temporaire rapide, ou pour le transfert d’octets bruts ou d’objets sérialisés entre des processus indépendants.

Les fichiers de mémoire partagée diffèrent des autres fichiers mémoire dans la mémoire qui leur est allouée avec la fonction Windows [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) . La `CSharedFile` classe stocke les données dans un bloc de mémoire alloué globalement (créé à l’aide de `GlobalAlloc` ), et ce bloc de mémoire peut être partagé à l’aide de DDE, du presse-papiers ou d’autres opérations de transfert de données uniforme OLE/com, par exemple, à l’aide de `IDataObject` .

`GlobalAlloc` retourne un handle HGLOBAL plutôt qu’un pointeur vers la mémoire, tel que le pointeur retourné par [malloc](../../c-runtime-library/reference/malloc.md). Le descripteur HGLOBAL est nécessaire dans certaines applications. Par exemple, pour placer des données dans le presse-papiers, vous avez besoin d’un handle HGLOBAL.

`CSharedFile` n’utilise pas de fichiers mappés en mémoire et les données ne peuvent pas être partagées directement entre les processus.

`CSharedFile` les objets peuvent automatiquement allouer leur propre mémoire. Ou vous pouvez attacher votre propre bloc de mémoire à l' `CSharedFile` objet en appelant [CSharedFile :: SetHandle](#sethandle). Dans les deux cas, la mémoire pour augmenter automatiquement le fichier de mémoire est allouée aux `nGrowBytes` incréments par taille si `nGrowBytes` n’est pas égal à zéro.

Pour plus d’informations, consultez l’article [fichiers dans MFC](../../mfc/files-in-mfc.md) et [gestion des fichiers](../../c-runtime-library/file-handling.md) dans la référence de la *bibliothèque Runtime*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>Spécifications

**En-tête :** afxadv. h

## <a name="csharedfilecsharedfile"></a><a name="csharedfile"></a> CSharedFile::CSharedFile

Construit un `CSharedFile` objet et lui alloue de la mémoire.

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>Paramètres

*nAllocFlags*<br/>
Indicateurs indiquant comment la mémoire doit être allouée. Pour obtenir la liste des valeurs d’indicateur valides, consultez [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) .

*nGrowBytes*<br/>
Incrément d’allocation de mémoire en octets.

## <a name="csharedfiledetach"></a><a name="detach"></a> CSharedFile ::D Etach

Appelez cette fonction pour fermer le fichier de mémoire et le détacher du bloc de mémoire.

```
HGLOBAL Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Handle du bloc de mémoire qui contient le contenu du fichier de mémoire.

### <a name="remarks"></a>Notes

Vous pouvez le rouvrir en appelant [SetHandle](#sethandle), à l’aide du handle retourné par **Detach**.

## <a name="csharedfilesethandle"></a><a name="sethandle"></a> CSharedFile::SetHandle

Appelez cette fonction pour attacher un bloc de mémoire globale à l' `CSharedFile` objet.

```cpp
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>Paramètres

*hGlobalMemory*<br/>
Handle de la mémoire globale à attacher à `CSharedFile` .

*bAllowGrow*<br/>
Spécifie si le bloc de mémoire est autorisé à croître.

### <a name="remarks"></a>Notes

Si *bAllowGrow* est différent de zéro, la taille du bloc de mémoire est augmentée si nécessaire, par exemple, si vous tentez d’écrire plus d’octets dans le fichier que la taille du bloc de mémoire.

## <a name="see-also"></a>Voir aussi

[CMemFile, classe](../../mfc/reference/cmemfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMemFile, classe](../../mfc/reference/cmemfile-class.md)
