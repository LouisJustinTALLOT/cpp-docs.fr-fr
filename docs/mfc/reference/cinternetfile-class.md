---
title: CInternetFile, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CInternetFile
- AFXINET/CInternetFile
- AFXINET/CInternetFile::CInternetFile
- AFXINET/CInternetFile::Abort
- AFXINET/CInternetFile::Close
- AFXINET/CInternetFile::Flush
- AFXINET/CInternetFile::GetLength
- AFXINET/CInternetFile::Read
- AFXINET/CInternetFile::ReadString
- AFXINET/CInternetFile::Seek
- AFXINET/CInternetFile::SetReadBufferSize
- AFXINET/CInternetFile::SetWriteBufferSize
- AFXINET/CInternetFile::Write
- AFXINET/CInternetFile::WriteString
- AFXINET/CInternetFile::m_hFile
dev_langs:
- C++
helpviewer_keywords:
- CInternetFile [MFC], CInternetFile
- CInternetFile [MFC], Abort
- CInternetFile [MFC], Close
- CInternetFile [MFC], Flush
- CInternetFile [MFC], GetLength
- CInternetFile [MFC], Read
- CInternetFile [MFC], ReadString
- CInternetFile [MFC], Seek
- CInternetFile [MFC], SetReadBufferSize
- CInternetFile [MFC], SetWriteBufferSize
- CInternetFile [MFC], Write
- CInternetFile [MFC], WriteString
- CInternetFile [MFC], m_hFile
ms.assetid: 96935681-ee71-4a8d-9783-5abc7b3e6f10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5a26b38943d6fe76031d85cc68fd705e0d739c8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071991"
---
# <a name="cinternetfile-class"></a>CInternetFile, classe

Autorise l’accès aux fichiers sur des systèmes distants qui utilisent des protocoles Internet.

## <a name="syntax"></a>Syntaxe

```
class CInternetFile : public CStdioFile
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CInternetFile::CInternetFile](#cinternetfile)|Construit un objet `CInternetFile`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CInternetFile::Abort](#abort)|Ferme le fichier, en ignorant toutes les erreurs et avertissements.|
|[CInternetFile::Close](#close)|Ferme un `CInternetFile` et libère ses ressources.|
|[CInternetFile::Flush](#flush)|Vide le contenu de la mémoire tampon d’écriture et permet de s’assurer que les données en mémoire sont écrites sur l’ordinateur cible.|
|[CInternetFile::GetLength](#getlength)|Retourne la taille du fichier.|
|[CInternetFile::Read](#read)|Lit le nombre d’octets spécifiés.|
|[CInternetFile::ReadString](#readstring)|Lit un flux de caractères.|
|[CInternetFile::Seek](#seek)|Repositionne le pointeur dans un fichier ouvert.|
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|Définit la taille de la mémoire tampon où les données seront lues.|
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|Définit la taille de la mémoire tampon dans laquelle les données seront écrites.|
|[CInternetFile::Write](#write)|Écrit le nombre d’octets spécifiés.|
|[CInternetFile::WriteString](#writestring)|Écrit une chaîne se terminant par null dans un fichier.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CInternetFile::operator HINTERNET](#operator_hinternet)|Un opérateur de cast pour un handle d’Internet.|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[CInternetFile::m_hFile](#m_hfile)|Handle vers un fichier.|

## <a name="remarks"></a>Notes

Fournit une classe de base pour le [CHttpFile](../../mfc/reference/chttpfile-class.md) et [CGopherFile](../../mfc/reference/cgopherfile-class.md) classes de fichier. Vous ne créez jamais un `CInternetFile` directement l’objet. Au lieu de cela, créez un objet d’un de ses classes dérivées en appelant [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) ou [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Vous pouvez également créer un `CInternetFile` objet en appelant [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

Le `CInternetFile` fonctions membres `Open`, `LockRange`, `UnlockRange`, et `Duplicate` ne sont pas implémentées pour `CInternetFile`. Si vous appelez ces fonctions sur un `CInternetFile` de l’objet, vous obtiendrez un [exception CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Pour en savoir plus sur la façon `CInternetFile` fonctionne avec les autres classes Internet de MFC, consultez l’article [Internet programmation avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxinet.h

##  <a name="abort"></a>  CInternetFile::Abort

Ferme le fichier associé à cet objet et rend le fichier indisponible pour la lecture ou écriture.

```
virtual void Abort();
```

### <a name="remarks"></a>Notes

Si vous n’avez pas fermé le fichier avant de détruire l’objet, le destructeur ferme pour vous.

Lors de la gestion des exceptions, `Abort` diffère [fermer](#close) de deux manières. Tout d’abord, le `Abort` fonction ne lève pas une exception en cas d’échec, car il ignore les échecs. Ensuite, `Abort` pas **ASSERT** si le fichier n’a pas été ouvert ou a été fermé précédemment.

##  <a name="cinternetfile"></a>  CInternetFile::CInternetFile

Cette fonction membre est appelée quand un `CInternetFile` objet est créé.

```
CInternetFile(
    HINTERNET hFile,
    LPCTSTR pstrFileName,
    CInternetConnection* pConnection,
    BOOL bReadMode);

CInternetFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrFileName,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext,
    BOOL bReadMode);
```

### <a name="parameters"></a>Paramètres

*hFile*<br/>
Handle vers un fichier d’Internet.

*pstrFileName*<br/>
Un pointeur vers une chaîne contenant le nom de fichier.

*pConnection*<br/>
Un pointeur vers un [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) objet.

*bReadMode*<br/>
Indique si le fichier est en lecture seule.

*hSession*<br/>
Handle vers une session Internet.

*pstrServer*<br/>
Un pointeur vers une chaîne contenant le nom du serveur.

*dwContext*<br/>
L’identificateur de contexte pour le `CInternetFile` objet. Consultez [fondamentaux relatifs à WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.

### <a name="remarks"></a>Notes

Vous ne créez jamais un `CInternetFile` directement l’objet. Au lieu de cela, créez un objet d’un de ses classes dérivées en appelant [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) ou [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Vous pouvez également créer un `CInternetFile` objet en appelant [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

##  <a name="close"></a>  CInternetFile::Close

Ferme un `CInternetFile` et libère ses ressources.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Si le fichier a été ouvert en écriture, il est un appel implicite à [vider](#flush) pour vous assurer que toutes les données de mises en mémoire est écrit à l’hôte. Vous devez appeler `Close` lorsque vous avez terminé à l’aide d’un fichier.

##  <a name="flush"></a>  CInternetFile::Flush

Appelez cette fonction membre pour vider le contenu de la mémoire tampon d’écriture.

```
virtual void Flush();
```

### <a name="remarks"></a>Notes

Utilisez `Flush` pour s’assurer que toutes les données en mémoire a réellement été écrits dans l’ordinateur cible et pour garantir votre transaction avec l’ordinateur hôte a été effectuée. `Flush` est uniquement efficace sur `CInternetFile` objets ouvert en écriture.

##  <a name="getlength"></a>  CInternetFile::GetLength

Retourne la taille du fichier.

```
virtual ULONGLONG GetLength() const;
```

##  <a name="m_hfile"></a>  CInternetFile::m_hFile

Handle vers le fichier associé à cet objet.

```
HINTERNET m_hFile;
```

##  <a name="operator_hinternet"></a>  CInternetFile::operator HINTERNET

Utilisez cet opérateur pour obtenir le handle de Windows pour la session Internet actuelle.

```
operator HINTERNET() const;
```

##  <a name="read"></a>  CInternetFile::Read

Appelez cette fonction membre pour lire dans la mémoire spécifiée, en commençant à *lpvBuf*, le nombre d’octets, spécifié *nCount*.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Pointeur désignant une adresse mémoire où sont lues des données de fichier.

*nCount*<br/>
Nombre d'octets à écrire.

### <a name="return-value"></a>Valeur de retour

Nombre d'octets transférés dans la mémoire tampon. La valeur de retour peut être inférieure à *nCount* si la fin du fichier a été atteinte.

### <a name="remarks"></a>Notes

La fonction retourne le nombre d’octets réellement lus, un nombre qui peut être inférieur à *nCount* si le fichier se termine. Si une erreur se produit lors de la lecture du fichier, la fonction lève un [CInternetException](../../mfc/reference/cinternetexception-class.md) objet qui décrit l’erreur. Notez que la lecture au-delà de la fin du fichier n'est pas considérée comme une erreur et aucune exception n'est levée.

Pour garantir que toutes les données sont récupérées, une application doit continuer à appeler le `CInternetFile::Read` méthode jusqu'à ce que la méthode retourne la valeur zéro.

##  <a name="readstring"></a>  CInternetFile::ReadString

Appelez cette fonction membre pour lire un flux de caractères jusqu'à ce qu’il trouve un caractère de saut de ligne.

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>Paramètres

*pStr*<br/>
Un pointeur vers une chaîne qui reçoit la ligne en cours de lecture.

*nombre maximal*<br/>
Le nombre maximal de caractères à lire.

*rString*<br/>
Une référence à la [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet qui reçoit la ligne de lecture.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la mémoire tampon contenant les données ordinaires récupérées à partir de la [CInternetFile](../../mfc/reference/cinternetfile-class.md) objet. Quel que soit le type de données de la mémoire tampon passée à cette méthode, il n’effectue pas des manipulations sur les données (par exemple, la conversion en Unicode), donc vous devez mapper les données retournées à la structure que vous attendez, comme si le **void** <strong>\*</strong> type ont été retournés.

NULL si la fin du fichier a été atteinte sans lire toutes les données ; ou, si le booléen, FALSE si la fin du fichier a été atteinte sans lire toutes les données.

### <a name="remarks"></a>Notes

La fonction place la ligne qui en résulte dans la mémoire référencée par le *pstr* paramètre. Il s’arrête de lire des caractères lorsqu’il atteint le nombre maximal de caractères, spécifié par *nMax*. La mémoire tampon reçoit toujours un caractère null de fin.

Si vous appelez `ReadString` sans appeler d’abord [SetReadBufferSize](#setreadbuffersize), vous obtiendrez une mémoire tampon de 4 096 octets.

##  <a name="seek"></a>  CInternetFile::Seek

Appelez cette fonction membre pour repositionner le pointeur dans un fichier ouvert précédemment.

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>Paramètres

*lOffset*<br/>
Décalage en octets pour déplacer le pointeur de lecture/écriture dans le fichier.

*Ndepuis*<br/>
Référence relative pour le décalage. Doit être une des valeurs suivantes :

- `CFile::begin` Déplacez le pointeur de fichier *lOff* octets transférer à partir du début du fichier.

- `CFile::current` Déplacez le pointeur de fichier *lOff* octets à partir de la position actuelle dans le fichier.

- `CFile::end` Déplacez le pointeur de fichier *lOff* octets à partir de la fin du fichier. *lOff* doit être négatif à rechercher dans l’existant de fichiers ; positif valeurs cherchera au-delà de la fin du fichier.

### <a name="return-value"></a>Valeur de retour

Le nouveau décalage d’octet du début du fichier si la position demandée est légale. Sinon, la valeur est indéfinie et un [CInternetException](../../mfc/reference/cinternetexception-class.md) objet est levé.

### <a name="remarks"></a>Notes

Le `Seek` fonction autorise l’accès aléatoire au contenu d’un fichier en déplaçant le pointeur une quantité spécifiée, relative ou absolue. Aucune donnée n’est lue pendant la recherche.

À ce stade, un appel à cette fonction membre n’est possible que des données associées `CHttpFile` objets. Il n’est pas pris en charge pour les demandes FTP ou gopher. Si vous appelez `Seek` pour un de ces services non pris en charge, il vous passera revenir au code d’erreur Win32 ERROR_INTERNET_INVALID_OPERATION.

Lorsqu’un fichier est ouvert, le pointeur de fichier est à l’offset 0, le début du fichier.

> [!NOTE]
>  À l’aide de `Seek` peut entraîner un appel implicite à [vider](#flush).

### <a name="example"></a>Exemple

  Consultez l’exemple pour l’implémentation de classe de base ( [CFile::Seek](../../mfc/reference/cfile-class.md#seek)).

##  <a name="setreadbuffersize"></a>  CInternetFile::SetReadBufferSize

Appelez cette fonction membre pour définir la taille du tampon de lecture temporaire utilisé par un `CInternetFile`-objet dérivé.

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>Paramètres

*nReadSize*<br/>
Taille de la mémoire tampon voulue en octets.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

APIs WinInet sous-jacentes ne pas effectuer la mise en mémoire tampon, par conséquent, choisissez une taille de mémoire tampon qui permet à votre application lire les données de manière efficace, quelle que soit la quantité de données à lire. Si chaque appel à [en lecture](#read) normalement implique un aount volumineux de données (par exemple, les kilo-octets quatre ou plus), vous ne devez pas une mémoire tampon. Toutefois, si vous appelez `Read` pour obtenir des petits morceaux de données, ou si vous utilisez [ReadString](#readstring) pour lire des lignes individuelles à la fois, d’un mémoire tampon de lecture améliore les performances de l’application.

Par défaut, un `CInternetFile` objet ne fournit pas de toute mise en mémoire tampon pour la lecture. Si vous appelez cette fonction membre, vous devez être sûr que le fichier a été ouvert pour un accès en lecture.

Vous pouvez augmenter la taille du tampon à tout moment, mais la réduction de la mémoire tampon n’a aucun effet. Si vous appelez [ReadString](#readstring) sans appeler d’abord `SetReadBufferSize`, vous obtiendrez une mémoire tampon de 4 096 octets.

##  <a name="setwritebuffersize"></a>  CInternetFile::SetWriteBufferSize

Appelez cette fonction membre pour définir la taille de la mémoire tampon d’écriture temporaire utilisé par un `CInternetFile`-objet dérivé.

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>Paramètres

*nWriteSize*<br/>
Taille de la mémoire tampon en octets.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Sous-jacent WinInet APIs n’effectuez pas de mise en mémoire tampon, choisissez donc une taille de mémoire tampon qui permet à votre application écrire des données efficacement, quel que soit la quantité de données à écrire. Si chaque appel à [écrire](#write) normalement implique une grande quantité de données (par exemple, les kilo-octets quatre ou plus à la fois), vous ne devez pas une mémoire tampon. Toutefois, si vous appelez [écrire](#write) pour écrire des petits morceaux de données, une mémoire tampon d’écriture améliore les performances de votre application.

Par défaut, un `CInternetFile` objet ne fournit pas de toute mise en mémoire tampon pour l’écriture. Si vous appelez cette fonction membre, vous devez être sûr que le fichier a été ouvert pour un accès en écriture. Vous pouvez modifier la taille de la mémoire tampon d’écriture à tout moment, mais cela entraîne un appel implicite à [vider](#flush).

##  <a name="write"></a>  CInternetFile::Write

Appelez cette fonction membre à écrire dans la mémoire spécifiée, *lpvBuf*, le nombre d’octets, spécifié *nCount*.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Un pointeur vers le premier octet à écrire.

*nCount*<br/>
Spécifie le nombre d’octets à écrire.

### <a name="remarks"></a>Notes

Si une erreur se produit lors de l’écriture des données, la fonction lève un [CInternetException](../../mfc/reference/cinternetexception-class.md) objet décrivant l’erreur.

##  <a name="writestring"></a>  CInternetFile::WriteString

Cette fonction écrit une chaîne se terminant par null dans le fichier associé.

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>Paramètres

*pStr*<br/>
Un pointeur vers une chaîne contenant le contenu à écrire.

### <a name="remarks"></a>Notes

Si une erreur se produit lors de l’écriture des données, la fonction lève un [CInternetException](../../mfc/reference/cinternetexception-class.md) objet décrivant l’erreur.

## <a name="see-also"></a>Voir aussi

[CStdioFile, classe](../../mfc/reference/cstdiofile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)
