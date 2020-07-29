---
title: CInternetFile, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 460130d98fc9bce761ee293e1a46c86c770b24c9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223068"
---
# <a name="cinternetfile-class"></a>CInternetFile, classe

Autorise l’accès aux fichiers sur les systèmes distants qui utilisent des protocoles Internet.

## <a name="syntax"></a>Syntaxe

```
class CInternetFile : public CStdioFile
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CInternetFile :: CInternetFile](#cinternetfile)|Construit un objet `CInternetFile`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CInternetFile :: Abort](#abort)|Ferme le fichier en ignorant tous les avertissements et erreurs.|
|[CInternetFile :: Close](#close)|Ferme `CInternetFile` et libère ses ressources.|
|[CInternetFile :: Flush](#flush)|Vide le contenu de la mémoire tampon d’écriture et vérifie que les données en mémoire sont écrites sur l’ordinateur cible.|
|[CInternetFile :: GetLength](#getlength)|Retourne la taille du fichier.|
|[CInternetFile :: Read](#read)|Lit le nombre d’octets spécifiés.|
|[CInternetFile :: ReadString](#readstring)|Lit un flux de caractères.|
|[CInternetFile :: Seek](#seek)|Repositionne le pointeur dans un fichier ouvert.|
|[CInternetFile :: SetReadBufferSize](#setreadbuffersize)|Définit la taille de la mémoire tampon dans laquelle les données sont lues.|
|[CInternetFile :: SetWriteBufferSize](#setwritebuffersize)|Définit la taille de la mémoire tampon dans laquelle les données seront écrites.|
|[CInternetFile :: Write](#write)|Écrit le nombre d’octets spécifiés.|
|[CInternetFile :: WriteString](#writestring)|Écrit une chaîne se terminant par un caractère NULL dans un fichier.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CInternetFile :: Operator HINTERNET](#operator_hinternet)|Opérateur de cast pour un handle Internet.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CInternetFile :: m_hFile](#m_hfile)|Handle d’un fichier.|

## <a name="remarks"></a>Notes

Fournit une classe de base pour les classes de fichier [CHttpFile](../../mfc/reference/chttpfile-class.md) et [CGopherFile](../../mfc/reference/cgopherfile-class.md) . Vous ne devez jamais créer un `CInternetFile` objet directement. Au lieu de cela, créez un objet de l’une de ses classes dérivées en appelant [CGopherConnection :: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) ou [CHttpConnection :: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Vous pouvez également créer un `CInternetFile` objet en appelant [CFtpConnection :: OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

Les `CInternetFile` fonctions membres `Open` , `LockRange` , `UnlockRange` et ne `Duplicate` sont pas implémentées pour `CInternetFile` . Si vous appelez ces fonctions sur un `CInternetFile` objet, vous obtiendrez un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Pour en savoir plus sur le `CInternetFile` fonctionnement des autres classes Internet MFC, consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXINET. h

## <a name="cinternetfileabort"></a><a name="abort"></a>CInternetFile :: Abort

Ferme le fichier associé à cet objet et rend le fichier indisponible pour la lecture ou l’écriture.

```
virtual void Abort();
```

### <a name="remarks"></a>Notes

Si vous n’avez pas fermé le fichier avant de détruire l’objet, le destructeur le ferme pour vous.

Lors de la gestion des exceptions, `Abort` diffère de [près](#close) de deux façons importantes. Tout d’abord, la `Abort` fonction ne lève pas d’exception en cas d’échec, car elle ignore les échecs. Deuxièmement, `Abort` ne **déclare** pas si le fichier n’a pas été ouvert ou a été fermé précédemment.

## <a name="cinternetfilecinternetfile"></a><a name="cinternetfile"></a>CInternetFile :: CInternetFile

Cette fonction membre est appelée lorsqu’un `CInternetFile` objet est créé.

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
Handle d’un fichier Internet.

*pstrFileName*<br/>
Pointeur vers une chaîne contenant le nom de fichier.

*pConnection*<br/>
Pointeur vers un objet [CInternetConnection,](../../mfc/reference/cinternetconnection-class.md) .

*bReadMode*<br/>
Indique si le fichier est en lecture seule.

*hSession*<br/>
Handle d’une session Internet.

*pstrServer*<br/>
Pointeur vers une chaîne contenant le nom du serveur.

*dwContext*<br/>
Identificateur de contexte de l' `CInternetFile` objet. Pour plus d’informations sur l’identificateur de contexte, consultez [concepts de base de WinInet](../../mfc/wininet-basics.md) .

### <a name="remarks"></a>Notes

Vous ne devez jamais créer un `CInternetFile` objet directement. Au lieu de cela, créez un objet de l’une de ses classes dérivées en appelant [CGopherConnection :: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) ou [CHttpConnection :: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Vous pouvez également créer un `CInternetFile` objet en appelant [CFtpConnection :: OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

## <a name="cinternetfileclose"></a><a name="close"></a>CInternetFile :: Close

Ferme `CInternetFile` et libère l’une de ses ressources.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Si le fichier a été ouvert en écriture, il existe un appel implicite à [flush](#flush) pour s’assurer que toutes les données mises en mémoire tampon sont écrites sur l’hôte. Vous devez appeler `Close` lorsque vous avez fini d’utiliser un fichier.

## <a name="cinternetfileflush"></a><a name="flush"></a>CInternetFile :: Flush

Appelez cette fonction membre pour vider le contenu de la mémoire tampon d’écriture.

```
virtual void Flush();
```

### <a name="remarks"></a>Notes

Utilisez `Flush` pour vous assurer que toutes les données en mémoire ont été écrites sur l’ordinateur cible et que votre transaction avec l’ordinateur hôte est terminée. `Flush`s’applique uniquement aux `CInternetFile` objets ouverts en écriture.

## <a name="cinternetfilegetlength"></a><a name="getlength"></a>CInternetFile :: GetLength

Retourne la taille du fichier.

```
virtual ULONGLONG GetLength() const;
```

## <a name="cinternetfilem_hfile"></a><a name="m_hfile"></a>CInternetFile :: m_hFile

Handle du fichier associé à cet objet.

```
HINTERNET m_hFile;
```

## <a name="cinternetfileoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetFile :: Operator HINTERNET

Utilisez cet opérateur pour obtenir le handle Windows pour la session Internet en cours.

```
operator HINTERNET() const;
```

## <a name="cinternetfileread"></a><a name="read"></a>CInternetFile :: Read

Appelez cette fonction membre pour lire dans la mémoire spécifiée, en commençant à *lpvBuf*, le nombre d’octets spécifié, *nCount*.

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

La fonction retourne le nombre d’octets réellement lus, un nombre qui peut être inférieur à *nCount* si le fichier se termine. Si une erreur se produit lors de la lecture du fichier, la fonction lève un objet [CInternetException](../../mfc/reference/cinternetexception-class.md) qui décrit l’erreur. Notez que la lecture au-delà de la fin du fichier n'est pas considérée comme une erreur et aucune exception n'est levée.

Pour vous assurer que toutes les données sont récupérées, une application doit continuer à appeler la `CInternetFile::Read` méthode jusqu’à ce que la méthode retourne zéro.

## <a name="cinternetfilereadstring"></a><a name="readstring"></a>CInternetFile :: ReadString

Appelez cette fonction membre pour lire un flux de caractères jusqu’à ce qu’il trouve un caractère de saut de ligne.

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>Paramètres

*pstr*<br/>
Pointeur vers une chaîne qui reçoit la ligne en cours de lecture.

*nMax*<br/>
Nombre maximal de caractères à lire.

*rString*<br/>
Référence à l’objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui reçoit la ligne de lecture.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la mémoire tampon qui contient les données brutes récupérées de l’objet [CInternetFile](../../mfc/reference/cinternetfile-class.md) . Quel que soit le type de données de la mémoire tampon passé à cette méthode, il n’effectue aucune manipulation sur les données (par exemple, la conversion en Unicode). vous devez donc mapper les données retournées à la structure attendue, comme si le **`void`** <strong>\*</strong> type était retourné.

NULL si la fin du fichier a été atteinte sans lire de données ; ou, si booléen, FALSe si la fin de fichier a été atteinte sans lire de données.

### <a name="remarks"></a>Notes

La fonction place la ligne résultante dans la mémoire référencée par le paramètre *PSTR* . Il arrête de lire les caractères lorsqu’il atteint le nombre maximal de caractères, spécifié par *nmax*. La mémoire tampon reçoit toujours un caractère null de fin.

Si vous appelez `ReadString` sans appeler [SetReadBufferSize](#setreadbuffersize)en premier, vous obtiendrez une mémoire tampon de 4096 octets.

## <a name="cinternetfileseek"></a><a name="seek"></a>CInternetFile :: Seek

Appelez cette fonction membre pour repositionner le pointeur dans un fichier précédemment ouvert.

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>Paramètres

*lOffset*<br/>
Décalage en octets pour déplacer le pointeur en lecture/écriture dans le fichier.

*Ndepuis*<br/>
Référence relative pour l’offset. Il doit s’agir de l’une des valeurs suivantes : 

- `CFile::begin`Déplacez le pointeur de fichier *lOff* d’octets vers l’avant à partir du début du fichier.

- `CFile::current`Déplacez le pointeur de fichier *lOff* octets à partir de la position actuelle dans le fichier.

- `CFile::end`Déplacez le pointeur de fichier *lOff* octets à partir de la fin du fichier. *lOff* doit être négatif pour effectuer une recherche dans le fichier existant ; les valeurs positives recherchent au-delà de la fin du fichier.

### <a name="return-value"></a>Valeur de retour

Nouvel offset d’octet à partir du début du fichier si la position demandée est conforme ; dans le cas contraire, la valeur est non définie et un objet [CInternetException](../../mfc/reference/cinternetexception-class.md) est levé.

### <a name="remarks"></a>Notes

La `Seek` fonction autorise l’accès aléatoire au contenu d’un fichier en déplaçant le pointeur d’une quantité spécifiée, de manière absolue ou relativement. Aucune donnée n’est réellement lue pendant la recherche.

À ce stade, un appel à cette fonction membre est uniquement pris en charge pour les données associées aux `CHttpFile` objets. Elle n’est pas prise en charge pour les demandes FTP ou gopher. Si vous appelez `Seek` pour l’un de ces services non pris en charge, il vous renvoie au code d’erreur Win32 ERROR_INTERNET_INVALID_OPERATION.

Lorsqu’un fichier est ouvert, le pointeur de fichier est au décalage 0, le début du fichier.

> [!NOTE]
> L’utilisation `Seek` de peut entraîner le [vidage](#flush)d’un appel implicite.

### <a name="example"></a>Exemple

  Consultez l’exemple correspondant à l’implémentation de la classe de base ( [CFile :: Seek](../../mfc/reference/cfile-class.md#seek)).

## <a name="cinternetfilesetreadbuffersize"></a><a name="setreadbuffersize"></a>CInternetFile :: SetReadBufferSize

Appelez cette fonction membre pour définir la taille de la mémoire tampon de lecture temporaire utilisée par un `CInternetFile` objet dérivé de.

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>Paramètres

*nReadSize*<br/>
Taille de la mémoire tampon voulue en octets.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Les API WinInet sous-jacentes n’effectuent pas de mise en mémoire tampon. par conséquent, choisissez une taille de mémoire tampon qui permet à votre application de lire les données efficacement, quelle que soit la quantité de données à lire. Si chaque appel à [Read](#read) implique normalement un grand aount de données (par exemple, quatre kilo-octets ou plus), vous ne devriez pas avoir besoin d’une mémoire tampon. Toutefois, si vous appelez `Read` pour obtenir de petites portions de données, ou si vous utilisez [ReadString](#readstring) pour lire des lignes individuelles à la fois, une mémoire tampon de lecture améliore les performances de l’application.

Par défaut, un `CInternetFile` objet ne fournit pas de mise en mémoire tampon pour la lecture. Si vous appelez cette fonction membre, vous devez vous assurer que le fichier a été ouvert pour l’accès en lecture.

Vous pouvez augmenter la taille de la mémoire tampon à tout moment, mais la réduction de la mémoire tampon n’aura aucun effet. Si vous appelez [ReadString](#readstring) sans appeler `SetReadBufferSize` en premier, vous obtiendrez une mémoire tampon de 4096 octets.

## <a name="cinternetfilesetwritebuffersize"></a><a name="setwritebuffersize"></a>CInternetFile :: SetWriteBufferSize

Appelez cette fonction membre pour définir la taille de la mémoire tampon d’écriture temporaire utilisée par un `CInternetFile` objet dérivé de.

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>Paramètres

*nWriteSize*<br/>
Taille de la mémoire tampon en octets.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Les API WinInet sous-jacentes n’effectuent pas de mise en mémoire tampon. par conséquent, choisissez une taille de mémoire tampon qui permet à votre application d’écrire des données efficacement, quelle que soit la quantité de données à écrire. Si chaque appel à [Write](#write) implique normalement une grande quantité de données (par exemple, au moins quatre kilo-octets à la fois), vous ne devriez pas avoir besoin d’une mémoire tampon. Toutefois, si vous appelez [Write](#write) pour écrire de petits blocs de données, un tampon d’écriture améliore les performances de votre application.

Par défaut, un `CInternetFile` objet ne fournit pas de mise en mémoire tampon pour l’écriture. Si vous appelez cette fonction membre, vous devez vous assurer que le fichier a été ouvert pour l’accès en écriture. Vous pouvez modifier la taille de la mémoire tampon d’écriture à tout moment, mais cela entraîne le [vidage](#flush)d’un appel implicite.

## <a name="cinternetfilewrite"></a><a name="write"></a>CInternetFile :: Write

Appelez cette fonction membre pour écrire dans la mémoire donnée, *lpvBuf*, le nombre d’octets spécifié, *nCount*.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Pointeur vers le premier octet à écrire.

*nCount*<br/>
Spécifie le nombre d’octets à écrire.

### <a name="remarks"></a>Notes

Si une erreur se produit lors de l’écriture des données, la fonction lève un objet [CInternetException](../../mfc/reference/cinternetexception-class.md) décrivant l’erreur.

## <a name="cinternetfilewritestring"></a><a name="writestring"></a>CInternetFile :: WriteString

Cette fonction écrit une chaîne se terminant par un caractère NULL dans le fichier associé.

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>Paramètres

*pstr*<br/>
Pointeur vers une chaîne contenant le contenu à écrire.

### <a name="remarks"></a>Notes

Si une erreur se produit lors de l’écriture des données, la fonction lève un objet [CInternetException](../../mfc/reference/cinternetexception-class.md) décrivant l’erreur.

## <a name="see-also"></a>Voir aussi

[CStdioFile, classe](../../mfc/reference/cstdiofile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection,, classe](../../mfc/reference/cinternetconnection-class.md)
