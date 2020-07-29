---
title: CMemFile, classe
description: Décrit les fonctions disponibles dans la classe CMemFile qui vous permettent d’utiliser des fichiers de mémoire.
ms.date: 07/23/2020
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CmemFile::GetBufferPtr
- AFX/CMemFile::GrowFile"
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GetBufferPtr
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
ms.openlocfilehash: edd1d8b8d3979427602bdb61fc7647aec15d58b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222938"
---
# <a name="cmemfile-class"></a>CMemFile, classe

Classe dérivée de [CFile](../../mfc/reference/cfile-class.md)qui prend en charge les fichiers de mémoire.

## <a name="syntax"></a>Syntaxe

```
class CMemFile : public CFile
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMemFile :: CMemFile](#cmemfile)|Construit un objet de fichier de mémoire.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMemFile :: Attach](#attach)|Attache un bloc de mémoire à `CMemFile` .|
|[CMemFile ::D Etach](#detach)|Détache le bloc de mémoire de `CMemFile` et retourne un pointeur vers le bloc de mémoire détaché.|
|[CMemFile :: GetBufferPtr](#getbufferptr)|Obtient ou écrit dans la mémoire tampon qui stocke un fichier mémoire.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMemFile :: Alloc](#alloc)|Substituez pour modifier le comportement d’allocation de mémoire.|
|[CMemFile :: Free](#free)|Substituez pour modifier le comportement de désallocation de mémoire.|
|[CMemFile :: GrowFile](#growfile)|Substituez pour modifier le comportement lors de la croissance d’un fichier.|
|[CMemFile :: memcpy](#memcpy)|Substituez pour modifier le comportement de copie de mémoire lors de la lecture et de l’écriture de fichiers.|
|[CMemFile :: realloc](#realloc)|Substituez pour modifier le comportement de réallocation de mémoire.|

## <a name="remarks"></a>Notes

Ces fichiers de mémoire se comportent comme des fichiers disque, sauf que le fichier est stocké dans la mémoire RAM plutôt que sur le disque. Un fichier de mémoire est utile pour :

- stockage temporaire rapide
- transfert d’octets bruts entre des processus indépendants
- transfert d’objets sérialisés entre des processus indépendants

`CMemFile`les objets peuvent automatiquement allouer leur propre mémoire. Ou vous pouvez attacher votre propre bloc de mémoire à l' `CMemFile` objet en appelant [Attach](#attach). Dans les deux cas, la mémoire pour augmenter automatiquement le fichier de mémoire est allouée aux `nGrowBytes` incréments par taille si `nGrowBytes` n’est pas égal à zéro.

Le bloc de mémoire est automatiquement supprimé lors de la destruction de l' `CMemFile` objet si la mémoire a été initialement allouée par l' `CMemFile` objet ; sinon, vous êtes chargé de libérer la mémoire que vous avez attachée à l’objet.

Vous pouvez accéder au bloc de mémoire via le pointeur fourni lorsque vous le détachez de l' `CMemFile` objet en appelant [Detach](#detach).

L’utilisation la plus courante de `CMemFile` consiste à créer un `CMemFile` objet et à l’utiliser en appelant les fonctions membres [CFile](../../mfc/reference/cfile-class.md) . La création d’un `CMemFile` s’ouvre automatiquement : vous n’appelez pas [CFile :: Open](../../mfc/reference/cfile-class.md#open), qui est utilisé uniquement pour les fichiers de disque. Étant donné que `CMemFile` n’utilise pas un fichier de disque, le membre de données `CFile::m_hFile` n’est pas utilisé.

Les `CFile` fonctions membres [duplicate](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange)et [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) ne sont pas implémentées pour `CMemFile` . Si vous appelez ces fonctions sur un `CMemFile` objet, vous obtiendrez un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

`CMemFile`utilise les fonctions de la bibliothèque Runtime [malloc](../../c-runtime-library/reference/malloc.md), [realloc](../../c-runtime-library/reference/realloc.md)et Free pour allouer, réallouer et [libérer](../../c-runtime-library/reference/free.md) de la mémoire ; et le [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) intrinsèque pour bloquer la copie de la mémoire lors de la lecture et de l’écriture. Si vous souhaitez modifier ce comportement ou le comportement lorsque `CMemFile` augmente un fichier, dérivez votre propre classe de `CMemFile` et remplacez les fonctions appropriées.

Pour plus d’informations `CMemFile` sur, consultez les [Articles fichiers dans MFC](../../mfc/files-in-mfc.md) et gestion de la [mémoire (MFC)](../../mfc/memory-management.md) et consultez [gestion des fichiers](../../c-runtime-library/file-handling.md) dans la référence de la *bibliothèque Runtime*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>Spécifications

**En-tête :** AFX. h

## <a name="cmemfilealloc"></a><a name="alloc"></a>CMemFile :: Alloc

Cette fonction est appelée par les `CMemFile` fonctions membres.

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>Paramètres

*nBytes*<br/>
Nombre d’octets de mémoire à allouer.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le bloc de mémoire qui a été alloué, ou NULL en cas d’échec de l’allocation.

### <a name="remarks"></a>Notes

Substituez cette fonction pour implémenter l’allocation de mémoire personnalisée. Si vous remplacez cette fonction, vous souhaiterez probablement remplacer [gratuitement](#free) et [réallocation](#realloc) .

L’implémentation par défaut utilise la fonction [malloc](../../c-runtime-library/reference/malloc.md) de la bibliothèque Runtime pour allouer de la mémoire.

## <a name="cmemfileattach"></a><a name="attach"></a>CMemFile :: Attach

Appelez cette fonction pour attacher un bloc de mémoire à `CMemFile` .

```cpp
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Paramètres

*lpBuffer*<br/>
Pointeur vers la mémoire tampon à attacher `CMemFile` .

*nBufferSize*<br/>
Entier qui spécifie la taille de la mémoire tampon en octets.

*nGrowBytes*<br/>
Incrément d’allocation de mémoire en octets.

### <a name="remarks"></a>Notes

Cela entraîne l' `CMemFile` utilisation du bloc de mémoire comme fichier de mémoire.

Si *nGrowBytes* a la valeur 0, `CMemFile` définit la longueur du fichier sur *nBufferSize*. Cela signifie que les données dans le bloc de mémoire avant d’être attachées à `CMemFile` seront utilisées comme fichier. Les fichiers de mémoire créés de cette manière ne peuvent pas être augmentés.

Étant donné que le fichier ne peut pas être augmenté, veillez à ne pas `CMemFile` tenter d’augmenter la taille du fichier. Par exemple, n’appelez pas les `CMemFile` substitutions de [CFile : Write](../../mfc/reference/cfile-class.md#write) pour écrire au-delà de la fin ou n’appelez pas [CFile : SetLength](../../mfc/reference/cfile-class.md#setlength) avec une longueur supérieure à *nBufferSize*.

Si *nGrowBytes* est supérieur à 0, `CMemFile` ignore le contenu du bloc de mémoire que vous avez attaché. Vous devrez écrire le contenu du fichier de mémoire à partir de zéro à l’aide `CMemFile` de la substitution de `CFile::Write` . Si vous tentez d’écrire au-delà de la fin du fichier ou d’augmenter le fichier en appelant la `CMemFile` substitution de `CFile::SetLength` , `CMemFile` l’allocation de mémoire sera augmentée par incréments de *nGrowBytes*. L’augmentation de l’allocation de mémoire échoue si le bloc de mémoire que vous transmettez `Attach` n’a pas été alloué avec une méthode compatible avec [Alloc](#alloc). Pour être compatible avec l’implémentation par défaut de `Alloc` , vous devez allouer la mémoire avec la fonction de bibliothèque Runtime [malloc](../../c-runtime-library/reference/malloc.md) ou [calloc](../../c-runtime-library/reference/calloc.md).

## <a name="cmemfilecmemfile"></a><a name="cmemfile"></a>CMemFile :: CMemFile

La première surcharge ouvre un fichier de mémoire vide.

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Paramètres

*nGrowBytes*<br/>
Incrément d’allocation de mémoire en octets.

*lpBuffer* Pointeur vers une mémoire tampon qui reçoit des informations de la taille *nBufferSize*.

*nBufferSize*<br/>
Entier qui spécifie la taille de la mémoire tampon du fichier, en octets.

### <a name="remarks"></a>Notes

Le fichier est ouvert par le constructeur. N’appelez pas [CFile :: Open](../../mfc/reference/cfile-class.md#open).

La deuxième surcharge agit comme si vous utilisiez le premier constructeur et immédiatement appelé [Attach](#attach) avec les mêmes paramètres. Pour plus d'informations, consultez `Attach`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

## <a name="cmemfiledetach"></a><a name="detach"></a>CMemFile ::D Etach

Appelez cette fonction pour obtenir un pointeur vers le bloc de mémoire utilisé par `CMemFile` .

```
BYTE* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le bloc de mémoire qui contient le contenu du fichier de mémoire.

### <a name="remarks"></a>Notes

L’appel de cette fonction ferme également `CMemFile` . Vous pouvez rattacher le bloc de mémoire à `CMemFile` en appelant [Attach](#attach). Si vous souhaitez rattacher le fichier et utiliser les données qu’il contient, vous devez appeler [CFile :: GetLength](../../mfc/reference/cfile-class.md#getlength) pour obtenir la longueur du fichier avant d’appeler `Detach` . Si vous attachez un bloc de mémoire à pour pouvoir `CMemFile` utiliser ses données ( `nGrowBytes` = = 0), vous ne pouvez pas augmenter le fichier de mémoire.

## <a name="cmemfilefree"></a><a name="free"></a>CMemFile :: Free

Cette fonction est appelée par les `CMemFile` fonctions membres.

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>Paramètres

*lpMem*<br/>
Pointeur vers la mémoire à libérer.

### <a name="remarks"></a>Notes

Substituez cette fonction pour implémenter une désallocation de mémoire personnalisée. Si vous remplacez cette fonction, vous souhaiterez probablement remplacer [Alloc](#alloc) et [realloc](#realloc) également.

## <a name="cmemfilegetbufferptr"></a><a name="getbufferptr"></a>CMemFile :: GetBufferPtr

Obtient ou écrit dans la mémoire tampon qui stocke un fichier mémoire.

```cpp
virtual UINT GetBufferPtr(
    UINT nCommand,
    UINT nCount = 0,
    void** ppBufStart = NULL,
    void** ppBufMax = NULL
);
```

### <a name="parameters"></a>Paramètres

*nLigne*<br/>
[BufferCommand](buffercommand-enumeration.md) à effectuer ( `bufferCheck` , `bufferCommit` , `bufferRead` ou `bufferWrite` ).

*nCount*<br/>
Selon *nLigne*, nombre d’octets dans la mémoire tampon à lire, écrire ou valider. Lors de la lecture à partir de la mémoire tampon, spécifiez-1 pour retourner une mémoire tampon de la position actuelle jusqu’à la fin du fichier.

*ppBufStart*<br/>
à Début de la mémoire tampon. Doit être `NULL` lorsque *nLigne* est `bufferCommit` .

*ppBufMax*<br/>
à Fin de la mémoire tampon. Doit être `NULL` lorsque nLigne est `bufferCommit` .

### <a name="return-value"></a>Valeur de retour

| valeur de la *commande* | Valeur retournée |
|--|--|
| `buffercheck` | Retourne [bufferDirect](buffercommand-enumeration.md) si la mise en mémoire tampon directe est prise en charge, sinon 0. |
| `bufferCommit` | Retourne `0`. |
| `bufferRead` ou `bufferWrite` | Retourne le nombre d’octets dans l’espace de mémoire tampon retourné. *ppBufStart* et *ppBufMax* pointent vers le début et la fin de la mémoire tampon de lecture/écriture.  |

### <a name="remarks"></a>Notes

La position actuelle dans la mémoire tampon ( `m_nPosition` ) est avancée des manières suivantes, en fonction de *nLigne*:

| *nLigne* | position de la mémoire tampon |
|-|-|
| `bufferCommit` | La position actuelle avance de la taille de la mémoire tampon validée. |
| `bufferRead` | La position actuelle avance de la taille de la mémoire tampon de lecture. |

## <a name="cmemfilegrowfile"></a><a name="growfile"></a>CMemFile :: GrowFile

Cette fonction est appelée par plusieurs des `CMemFile` fonctions membres.

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>Paramètres

*dwNewLen*<br/>
Nouvelle taille du fichier de mémoire.

### <a name="remarks"></a>Notes

Vous pouvez la remplacer si vous souhaitez modifier la façon dont `CMemFile` augmente son fichier. L’implémentation par défaut appelle [realloc](#realloc) pour augmenter un bloc existant (ou [Alloc](#alloc) pour créer un bloc de mémoire), en allouant de la mémoire dans des multiples de la `nGrowBytes` valeur spécifiée dans le constructeur ou l’appel d' [attachement](#attach) .

## <a name="cmemfilememcpy"></a><a name="memcpy"></a>CMemFile :: memcpy

Cette fonction est appelée par les `CMemFile` substitutions de [CFile :: Read](../../mfc/reference/cfile-class.md#read) et [CFile :: Write](../../mfc/reference/cfile-class.md#write) pour transférer des données vers et depuis le fichier de mémoire.

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Paramètres

*lpMemTarget*<br/>
Pointeur vers le bloc de mémoire dans lequel la mémoire source sera copiée.

*lpMemSource*<br/>
Pointeur vers le bloc de mémoire source.

*nBytes*<br/>
Nombre d'octets à copier.

### <a name="return-value"></a>Valeur de retour

Une copie de *lpMemTarget*.

### <a name="remarks"></a>Notes

Substituez cette fonction si vous souhaitez modifier la façon dont `CMemFile` ces copies de mémoire sont copiées.

## <a name="cmemfilerealloc"></a><a name="realloc"></a>CMemFile :: realloc

Cette fonction est appelée par les `CMemFile` fonctions membres.

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Paramètres

*lpMem*<br/>
Pointeur vers le bloc de mémoire à réallouer.

*nBytes*<br/>
Nouvelle taille du bloc de mémoire.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le bloc de mémoire qui a été réalloué (et éventuellement déplacé), ou NULL en cas d’échec de la réallocation.

### <a name="remarks"></a>Notes

Substituez cette fonction pour implémenter la réallocation de mémoire personnalisée. Si vous remplacez cette fonction, vous souhaiterez probablement remplacer [Alloc](#alloc) et [Free](#free) également.

## <a name="see-also"></a>Voir aussi

[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
