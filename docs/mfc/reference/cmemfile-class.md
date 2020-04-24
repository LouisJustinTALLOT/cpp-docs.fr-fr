---
title: Classe CMemFile
ms.date: 11/04/2016
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CMemFile::GrowFile
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
ms.openlocfilehash: 1bd88ad17bdb047de4c344ab96f3d9aecbe23c31
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752634"
---
# <a name="cmemfile-class"></a>Classe CMemFile

La classe [dérivée de CFile](../../mfc/reference/cfile-class.md)qui prend en charge les fichiers mémoire.

## <a name="syntax"></a>Syntaxe

```
class CMemFile : public CFile
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMemFile::CMemFile](#cmemfile)|Construit un objet de fichier mémoire.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMemFile::Attach](#attach)|Attache un bloc de `CMemFile`mémoire à .|
|[CMemFile::Detach](#detach)|Détache le bloc de `CMemFile` mémoire et renvoie un pointeur au bloc de mémoire détaché.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMemFile::Alloc](#alloc)|Remplacement pour modifier le comportement d’allocation de mémoire.|
|[CMemFile::Gratuit](#free)|Remplacer pour modifier le comportement de deallocation de la mémoire.|
|[CMemFile::GrowFile](#growfile)|Remplacer pour modifier le comportement lors de la culture d’un fichier.|
|[CMemFile::Memcpy](#memcpy)|Remplacer pour modifier le comportement de copie de mémoire lors de la lecture et l’écriture de fichiers.|
|[CMemFile::Réalloc](#realloc)|Remplacement pour modifier le comportement de réaffectation de la mémoire.|

## <a name="remarks"></a>Notes

Ces fichiers mémoire se comportent comme des fichiers disque, sauf que le fichier est stocké dans la RAM plutôt que sur le disque. Un fichier mémoire est utile pour le stockage temporaire rapide ou pour le transfert d’octets bruts ou d’objets sérialisés entre des processus indépendants.

`CMemFile`les objets peuvent automatiquement allouer leur propre mémoire `CMemFile` ou vous pouvez attacher votre propre bloc de mémoire à l’objet en appelant [Attach](#attach). Dans les deux cas, la mémoire pour `nGrowBytes`la culture du fichier `nGrowBytes` mémoire est automatiquement allouée par incréments de taille si elle n’est pas nulle.

Le bloc mémoire sera automatiquement supprimé `CMemFile` lors de la destruction de `CMemFile` l’objet si la mémoire a été initialement attribuée par l’objet; sinon, vous êtes responsable de traiter la mémoire que vous avez attachée à l’objet.

Vous pouvez accéder au bloc mémoire à travers le `CMemFile` pointeur fourni lorsque vous le détachez de l’objet en appelant [Detach](#detach).

L’utilisation la `CMemFile` plus courante `CMemFile` est de créer un objet et de l’utiliser en appelant les fonctions des membres [CFile.](../../mfc/reference/cfile-class.md) Notez que `CMemFile` la création d’un ouvre automatiquement: vous n’appelez pas [CFile::Open](../../mfc/reference/cfile-class.md#open), qui n’est utilisé que pour les fichiers disque. Parce `CMemFile` que n’utilise pas de `CFile::m_hFile` fichier disque, le membre des données n’est pas utilisé.

Les `CFile` fonctions membres [Duplicate](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), `CMemFile`et [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) ne sont pas implémentées pour . Si vous appelez ces `CMemFile` fonctions sur un objet, vous obtiendrez un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

`CMemFile`utilise les fonctions de bibliothèque en temps d’exécution [malloc](../../c-runtime-library/reference/malloc.md), [réaffecter](../../c-runtime-library/reference/realloc.md), et [libre](../../c-runtime-library/reference/free.md) d’allouer, réaffecter, et traiter la mémoire; et le [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) intrinsèque pour bloquer la mémoire de copie lors de la lecture et l’écriture. Si vous souhaitez changer ce comportement ou `CMemFile` le comportement lors de `CMemFile` la croissance d’un fichier, dérivez votre propre classe et remplacez les fonctions appropriées.

Pour plus `CMemFile`d’informations sur , voir les articles [Fichiers dans MFC](../../mfc/files-in-mfc.md) et [Memory Management (MFC)](../../mfc/memory-management.md) et voir [Traitement des fichiers](../../c-runtime-library/file-handling.md) dans la référence de *bibliothèque Run-Time*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="cmemfilealloc"></a><a name="alloc"></a>CMemFile::Alloc

Cette fonction est `CMemFile` appelée par les fonctions des membres.

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>Paramètres

*nBytes (en)*<br/>
Nombre d’octets de mémoire à attribuer.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le bloc mémoire qui a été attribué, ou NULL si l’allocation a échoué.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour implémenter l’allocation de mémoire personnalisée. Si vous remplacez cette fonction, vous aurez probablement envie de remplacer [Free](#free) et [Realloc](#realloc) ainsi.

L’implémentation par défaut utilise la fonction de bibliothèque en temps d’exécution [pour](../../c-runtime-library/reference/malloc.md) allouer la mémoire.

## <a name="cmemfileattach"></a><a name="attach"></a>CMemFile::Attach

Appelez cette fonction pour attacher `CMemFile`un bloc de mémoire à .

```cpp
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Paramètres

*lpBuffer*<br/>
Pointeur vers le tampon `CMemFile`à attacher à .

*nBufferSize*<br/>
Un intégrant qui spécifie la taille du tampon dans les octets.

*nGrowBytes (en)*<br/>
L’augmentation de l’allocation de mémoire dans les octets.

### <a name="remarks"></a>Notes

Cela `CMemFile` provoque d’utiliser le bloc de mémoire comme fichier mémoire.

Si *nGrowBytes* est `CMemFile` 0, définira la longueur du fichier à *nBufferSize*. Cela signifie que les données dans le `CMemFile` bloc mémoire avant qu’elles ne soient jointes seront utilisées comme fichier. Les fichiers mémoire créés de cette manière ne peuvent pas être cultivés.

Étant donné que le fichier ne `CMemFile` peut pas être cultivé, veillez à ne pas provoquer pour tenter de développer le fichier. Par exemple, n’appelez `CMemFile` pas les remplacements de [CFile: Écrivez](../../mfc/reference/cfile-class.md#write) pour écrire au-delà de la fin ou n’appelez pas [CFile:SetLength](../../mfc/reference/cfile-class.md#setlength) avec une longueur plus longue que *nBufferSize*.

Si *nGrowBytes* est supérieur `CMemFile` à 0, ignorera le contenu du bloc de mémoire que vous avez attaché. Vous devrez écrire le contenu du fichier mémoire `CMemFile` à partir `CFile::Write`de zéro en utilisant la dérogation de . Si vous essayez d’écrire au-delà de la `CMemFile` fin du `CFile::SetLength` `CMemFile` fichier ou de développer le fichier en appelant la dérogation de , augmentera l’allocation de mémoire par incréments de *nGrowBytes*. La croissance de l’allocation de mémoire `Attach` échouera si le bloc de mémoire que vous passez à n’a pas été alloué avec une méthode compatible avec [Alloc](#alloc). Pour être compatible avec `Alloc`la mise en œuvre par défaut de , vous devez allouer la mémoire avec la fonction de bibliothèque en temps d’exécution [malloc](../../c-runtime-library/reference/malloc.md) ou [calloc](../../c-runtime-library/reference/calloc.md).

## <a name="cmemfilecmemfile"></a><a name="cmemfile"></a>CMemFile::CMemFile

La première surcharge ouvre un fichier mémoire vide.

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Paramètres

*nGrowBytes (en)*<br/>
L’augmentation de l’allocation de mémoire dans les octets.

*lpBuffe*r Pointer à un tampon qui reçoit des informations de la taille *nBufferSize*.

*nBufferSize*<br/>
Un intégrant qui spécifie la taille du tampon de fichier, dans les octets.

### <a name="remarks"></a>Notes

Notez que le fichier est ouvert par le constructeur et que vous ne devriez pas appeler [CFile::Open](../../mfc/reference/cfile-class.md#open).

La deuxième surcharge agit de la même façon que si vous utiliez le premier constructeur et immédiatement appelé [Attach](#attach) avec les mêmes paramètres. Pour plus d'informations, consultez `Attach`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

## <a name="cmemfiledetach"></a><a name="detach"></a>CMemFile::Detach

Appelez cette fonction pour obtenir un pointeur `CMemFile`pour le bloc de mémoire utilisé par .

```
BYTE* Detach();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le bloc mémoire qui contient le contenu du fichier mémoire.

### <a name="remarks"></a>Notes

Appeler cette fonction ferme `CMemFile`également le . Vous pouvez rattacher le `CMemFile` bloc de mémoire en appelant [Attach](#attach). Si vous souhaitez rattacher le fichier et utiliser les données qu’il y a, vous devez appeler `Detach` [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) pour obtenir la longueur du fichier avant d’appeler . Notez que si vous `CMemFile` attachez un bloc de `nGrowBytes` mémoire pour que vous puissiez utiliser ses données (0), alors vous ne serez pas en mesure de développer le fichier mémoire.

## <a name="cmemfilefree"></a><a name="free"></a>CMemFile::Gratuit

Cette fonction est `CMemFile` appelée par les fonctions des membres.

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>Paramètres

*lpMem (en)*<br/>
Pointeur à la mémoire à traiter.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour implémenter la traite de mémoire personnalisée. Si vous remplacez cette fonction, vous aurez probablement envie de remplacer [Alloc](#alloc) et [Realloc](#realloc) ainsi.

## <a name="cmemfilegrowfile"></a><a name="growfile"></a>CMemFile::GrowFile

Cette fonction est appelée `CMemFile` par plusieurs des fonctions membres.

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>Paramètres

*dwNewLen*<br/>
Nouvelle taille du fichier mémoire.

### <a name="remarks"></a>Notes

Vous pouvez le remplacer si vous `CMemFile` voulez changer la façon dont développe son fichier. La implémentation par défaut appelle [Realloc](#realloc) à développer un bloc existant (ou `nGrowBytes` [Alloc](#alloc) pour créer un bloc mémoire), allouant la mémoire dans les multiples de la valeur spécifiée dans le constructeur ou [l’appel d’attache.](#attach)

## <a name="cmemfilememcpy"></a><a name="memcpy"></a>CMemFile::Memcpy

Cette fonction est `CMemFile` appelée par les remplacements de [CFile::Lire](../../mfc/reference/cfile-class.md#read) et [CFile::Écrire](../../mfc/reference/cfile-class.md#write) pour transférer des données à et depuis le fichier mémoire.

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Paramètres

*lpMemTarget*<br/>
Pointeur vers le bloc de mémoire dans lequel la mémoire source sera copiée.

*lpMemSource (en)*<br/>
Pointeur vers le bloc de mémoire source.

*nBytes (en)*<br/>
Nombre d'octets à copier.

### <a name="return-value"></a>Valeur de retour

Une copie de *lpMemTarget*.

### <a name="remarks"></a>Notes

Remplacez cette fonction si vous voulez `CMemFile` changer la façon dont ces copies de mémoire.

## <a name="cmemfilerealloc"></a><a name="realloc"></a>CMemFile::Réalloc

Cette fonction est `CMemFile` appelée par les fonctions des membres.

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Paramètres

*lpMem (en)*<br/>
Un pointeur vers le bloc de mémoire à réaffecter.

*nBytes (en)*<br/>
Nouvelle taille pour le bloc de mémoire.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le bloc de mémoire qui a été réaffecté (et peut-être déplacé), ou NULL si la réaffectation a échoué.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour implémenter la réaffectation personnalisée de la mémoire. Si vous remplacez cette fonction, vous aurez probablement envie de remplacer [Alloc](#alloc) et [Free](#free) ainsi.

## <a name="see-also"></a>Voir aussi

[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
