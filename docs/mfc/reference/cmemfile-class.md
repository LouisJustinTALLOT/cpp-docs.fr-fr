---
title: Classe CMemFile | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81421c99623fd3ab0abde20b479ec1ba91c3f936
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368359"
---
# <a name="cmemfile-class"></a>Classe CMemFile
Le [CFile](../../mfc/reference/cfile-class.md)-classe dérivée qui prend en charge les fichiers de mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMemFile : public CFile  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMemFile::CMemFile](#cmemfile)|Construit un objet de fichier de mémoire.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMemFile::Attach](#attach)|Attache un bloc de mémoire à `CMemFile`.|  
|[CMemFile::Detach](#detach)|Détache le bloc de mémoire à partir de `CMemFile` et retourne un pointeur vers le bloc de mémoire détachée.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMemFile::Alloc](#alloc)|Remplacement pour modifier le comportement de l’allocation de mémoire.|  
|[CMemFile::Free](#free)|Remplacement pour modifier le comportement de désallocation de mémoire.|  
|[CMemFile::GrowFile](#growfile)|Remplacement pour modifier le comportement lors de l’agrandissement d’un fichier.|  
|[CMemFile::Memcpy](#memcpy)|Substituer pour modifier le comportement de copie de mémoire lors de la lecture et écriture de fichiers.|  
|[CMemFile::Realloc](#realloc)|Remplacement pour modifier le comportement des opérations de réallocation de mémoire.|  
  
## <a name="remarks"></a>Notes  
 Ces fichiers de mémoire se comportent comme les fichiers de disque, sauf que le fichier est stocké dans la mémoire RAM, plutôt que sur le disque. Un fichier de mémoire est utile pour le stockage temporaire rapide ou le transfert d’octets bruts ou objets sérialisés entre des processus indépendants.  
  
 `CMemFile` objets peuvent allouer automatiquement leur propre mémoire, ou vous pouvez attacher votre propre bloc de mémoire à la `CMemFile` objet en appelant [attacher](#attach). Dans les deux cas, la mémoire pour la croissance d’automatiquement le fichier de mémoire est allouée dans `nGrowBytes`-taille par incréments si `nGrowBytes` n’est pas zéro.  
  
 Le bloc de mémoire sera automatiquement supprimé lors de la destruction de la `CMemFile` si la mémoire a été initialement allouée par l’objet le `CMemFile` de l’objet ; sinon, vous êtes chargé de libérer la mémoire que vous avez joint à l’objet.  
  
 Le bloc de mémoire accessible via le pointeur fourni lorsque vous détachez depuis le `CMemFile` objet en appelant [détachement](#detach).  
  
 L’utilisation la plus courante de `CMemFile` consiste à créer un `CMemFile` de l’objet et l’utiliser en appelant [CFile](../../mfc/reference/cfile-class.md) fonctions membres. Notez que la création d’un `CMemFile` s’ouvre automatiquement : vous n’appelez pas [CFile::Open](../../mfc/reference/cfile-class.md#open), qui est utilisé uniquement pour les fichiers de disque. Étant donné que `CMemFile` n’utilise pas un fichier de disque, le membre de données `CFile::m_hFile` n’est pas utilisé.  
  
 Le `CFile` fonctions membres [dupliquer](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), et [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) ne sont pas implémentées pour `CMemFile`. Si vous appelez ces fonctions sur un `CMemFile` de l’objet, vous obtiendrez un [exception CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 `CMemFile` utilise les fonctions de bibliothèque Runtime [malloc](../../c-runtime-library/reference/malloc.md), [realloc](../../c-runtime-library/reference/realloc.md), et [libre](../../c-runtime-library/reference/free.md) pour allouer, réallouer et désallouer la mémoire ; et la fonction intrinsèque [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) en bloc copie mémoire lors de la lecture et en écriture. Si vous souhaitez modifier ce comportement ou le comportement lorsque `CMemFile` augmente d’un fichier, dérivez votre propre classe de `CMemFile` et remplacer les fonctions appropriées.  
  
 Pour plus d’informations sur `CMemFile`, consultez les articles [fichiers dans MFC](../../mfc/files-in-mfc.md) et [gestion de mémoire (MFC)](../../mfc/memory-management.md) et [gestion des fichiers](../../c-runtime-library/file-handling.md) dans le *Run-Time Référence de la bibliothèque*.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CMemFile`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h  
  
##  <a name="alloc"></a>  CMemFile::Alloc  
 Cette fonction est appelée par `CMemFile` fonctions membres.  
  
```  
virtual BYTE* Alloc(SIZE_T nBytes);
```  
  
### <a name="parameters"></a>Paramètres  
 `nBytes`  
 Nombre d’octets de mémoire à allouer.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le bloc de mémoire qui a été alloué, ou **NULL** si l’allocation a échoué.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour implémenter l’allocation de mémoire personnalisée. Si vous remplacez cette fonction, vous souhaiterez probablement substituer [libre](#free) et [Realloc](#realloc) également.  
  
 L’implémentation par défaut utilise la fonction de la bibliothèque Runtime [malloc](../../c-runtime-library/reference/malloc.md) pour allouer de la mémoire.  
  
##  <a name="attach"></a>  CMemFile::Attach  
 Appelez cette fonction pour attacher un bloc de mémoire à `CMemFile`.  
  
```  
void Attach(
    BYTE* lpBuffer,  
    UINT nBufferSize,  
    UINT nGrowBytes = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpBuffer`  
 Pointeur vers la mémoire tampon à joindre à `CMemFile`.  
  
 `nBufferSize`  
 Entier qui spécifie la taille de la mémoire tampon en octets.  
  
 `nGrowBytes`  
 L’incrément de l’allocation de mémoire en octets.  
  
### <a name="remarks"></a>Notes  
 Cela entraîne `CMemFile` à utiliser le bloc de mémoire que le fichier de mémoire.  
  
 Si `nGrowBytes` est 0, `CMemFile` provoquera la longueur du fichier `nBufferSize`. Cela signifie que les données dans le bloc de mémoire avant qu’il a été attaché à `CMemFile` sera utilisé comme le fichier. Mémoire créé de cette manière ne peut pas être augmenté.  
  
 Étant donné que le fichier ne peut pas être agrandi, veillez à ne pas créer de `CMemFile` pour tenter de croissance du fichier. Par exemple, n’appelez pas la `CMemFile` substitue de [CFile:Write](../../mfc/reference/cfile-class.md#write) à écrire au-delà de la fin ou n’appelez pas [CFile:SetLength](../../mfc/reference/cfile-class.md#setlength) avec une longueur supérieure à `nBufferSize`.  
  
 Si `nGrowBytes` est supérieur à 0, `CMemFile` ignore le contenu du bloc de mémoire que vous avez joint. Vous devrez écrire le contenu du fichier en mémoire à partir de rien en utilisant le `CMemFile` la substitution de `CFile::Write`. Si vous tentez d’écrire au-delà de la fin du fichier ou la croissance du fichier en appelant le `CMemFile` la substitution de `CFile::SetLength`, `CMemFile` augmentera l’allocation de mémoire par incréments de `nGrowBytes`. Agrandissement de l’allocation de mémoire échoue si le bloc de mémoire que vous passez à **Attach** n’a pas été alloué avec une méthode compatible avec [Alloc](#alloc). Pour être compatible avec l’implémentation par défaut de `Alloc`, vous devez allouer la mémoire avec la fonction de la bibliothèque Runtime [malloc](../../c-runtime-library/reference/malloc.md) ou [calloc](../../c-runtime-library/reference/calloc.md).  
  
##  <a name="cmemfile"></a>  CMemFile::CMemFile  
 La première surcharge ouvre un fichier de mémoire vide.  
  
```  
CMemFile(UINT nGrowBytes = 1024);

 
CMemFile(
    BYTE* lpBuffer,  
    UINT nBufferSize,  
    UINT nGrowBytes = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 `nGrowBytes`  
 L’incrément de l’allocation de mémoire en octets.  
  
 *lpBuffe*r  
 Pointeur vers une mémoire tampon qui reçoit des informations de la taille `nBufferSize`.  
  
 `nBufferSize`  
 Entier qui spécifie la taille de la mémoire tampon de fichier, en octets.  
  
### <a name="remarks"></a>Notes  
 Notez que le fichier est ouvert par le constructeur, et que vous ne devez pas appeler [CFile::Open](../../mfc/reference/cfile-class.md#open).  
  
 La deuxième surcharge comporte comme si vous utilisé le premier constructeur et immédiatement appelé [attacher](#attach) avec les mêmes paramètres. Consultez **attacher** pour plus d’informations.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]  
  
##  <a name="detach"></a>  CMemFile::Detach  
 Appelez cette fonction pour obtenir un pointeur vers le bloc de mémoire utilisé par `CMemFile`.  
  
```  
BYTE* Detach();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le bloc de mémoire qui contient le contenu du fichier en mémoire.  
  
### <a name="remarks"></a>Notes  
 Appel de cette fonction se ferme également la `CMemFile`. Vous pouvez rattacher le bloc de mémoire `CMemFile` en appelant [attacher](#attach). Si vous souhaitez rattacher le fichier et d’utiliser les données qu’elle contient, vous devez appeler [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) pour obtenir la longueur du fichier avant d’appeler **détachement**. Notez que si vous attachez un bloc de mémoire `CMemFile` afin que vous puissiez utiliser ses données ( `nGrowBytes` == 0), puis vous ne pourrez pas la croissance du fichier de mémoire.  
  
##  <a name="free"></a>  CMemFile::Free  
 Cette fonction est appelée par `CMemFile` fonctions membres.  
  
```  
virtual void Free(BYTE* lpMem);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpMem`  
 Pointeur vers la mémoire à libérer.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour implémenter la désallocation de mémoire personnalisée. Si vous remplacez cette fonction, vous souhaiterez probablement substituer [Alloc](#alloc) et [Realloc](#realloc) également.  
  
##  <a name="growfile"></a>  CMemFile::GrowFile  
 Cette fonction est appelée par plusieurs le `CMemFile` fonctions membres.  
  
```  
virtual void GrowFile(SIZE_T dwNewLen);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwNewLen`  
 Nouvelle taille du fichier en mémoire.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez le remplacer si vous souhaitez modifier comment `CMemFile` augmente son fichier. L’implémentation par défaut appelle [Realloc](#realloc) atteindre un bloc existant (ou [Alloc](#alloc) pour créer un bloc de mémoire), allocation de mémoire par multiples de la `nGrowBytes` valeur spécifiée dans le constructeur ou [Attacher](#attach) appeler.  
  
##  <a name="memcpy"></a>  CMemFile::Memcpy  
 Cette fonction est appelée par le `CMemFile` substitue de [CFile::Read](../../mfc/reference/cfile-class.md#read) et [CFile::Write](../../mfc/reference/cfile-class.md#write) pour transférer des données vers et depuis le fichier de mémoire.  
  
```  
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,  
    const BYTE* lpMemSource,  
    SIZE_T nBytes);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpMemTarget`  
 Pointeur vers le bloc de mémoire dans laquelle la mémoire de la source sera copiée.  
  
 `lpMemSource`  
 Pointeur vers le bloc de mémoire source.  
  
 `nBytes`  
 Nombre d'octets à copier.  
  
### <a name="return-value"></a>Valeur de retour  
 Copie de l'objet `lpMemTarget`.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction si vous souhaitez modifier la façon dont qui `CMemFile` est ces copies de la mémoire.  
  
##  <a name="realloc"></a>  CMemFile::Realloc  
 Cette fonction est appelée par `CMemFile` fonctions membres.  
  
```  
virtual BYTE* Realloc(
    BYTE* lpMem,  
    SIZE_T nBytes);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpMem`  
 Pointeur vers le bloc de mémoire à réallouer.  
  
 `nBytes`  
 Nouvelle taille pour le bloc de mémoire.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le bloc de mémoire réalloué (et éventuellement déplacé), ou **NULL** en cas d’échec de la réallocation.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour implémenter les opérations de réallocation mémoire personnalisé. Si vous remplacez cette fonction, vous souhaiterez probablement substituer [Alloc](#alloc) et [libre](#free) également.  
  
## <a name="see-also"></a>Voir aussi  
 [CFile (classe)](../../mfc/reference/cfile-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



