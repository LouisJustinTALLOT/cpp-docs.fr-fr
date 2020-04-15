---
title: Classe CInternetFile
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
ms.openlocfilehash: e3f1a7167f5464423754951764c4441513197841
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372400"
---
# <a name="cinternetfile-class"></a>Classe CInternetFile

Permet l’accès aux fichiers sur les systèmes distants qui utilisent des protocoles Internet.

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
|[CInternetFile::Abort](#abort)|Ferme le fichier, ignorant tous les avertissements et erreurs.|
|[CInternetFile::Fermer](#close)|Ferme un `CInternetFile` et libère ses ressources.|
|[CInternetFile::Flush](#flush)|Rincer le contenu du tampon d’écriture et s’assure que les données en mémoire sont écrites à la machine cible.|
|[CInternetFile::GetLength](#getlength)|Retourne la taille du fichier.|
|[CInternetFile::Lire](#read)|Lit le nombre d’octets spécifiés.|
|[CInternetFile::LireString](#readstring)|Lit un flux de personnages.|
|[CInternetFile::Chercher](#seek)|Repositionne le pointeur dans un fichier ouvert.|
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|Définit la taille du tampon où les données seront lues.|
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|Définit la taille du tampon où les données seront écrites.|
|[CInternetFile::Ecrire](#write)|Écrit le nombre d’octets spécifiés.|
|[CInternetFile::WriteString](#writestring)|Écrit une corde non résiliée à un fichier.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CInternetFile::opérateur HINTERNET](#operator_hinternet)|Un opérateur de casting pour une poignée Internet.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CInternetFile::m_hFile](#m_hfile)|Une poignée à un fichier.|

## <a name="remarks"></a>Notes

Fournit une classe de base pour les classes de fichiers [CHttpFile](../../mfc/reference/chttpfile-class.md) et [CGopherFile.](../../mfc/reference/cgopherfile-class.md) Vous ne `CInternetFile` créez jamais un objet directement. Au lieu de cela, créer un objet de l’une de ses classes dérivées en appelant [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) ou [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Vous pouvez également `CInternetFile` créer un objet en appelant [CFtpConnection:OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

Les `CInternetFile` fonctions `Open` `LockRange`de `UnlockRange`membre, , , et `Duplicate` ne sont pas mis en œuvre pour `CInternetFile`. Si vous appelez ces `CInternetFile` fonctions sur un objet, vous obtiendrez un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Pour en savoir `CInternetFile` plus sur la façon dont fonctionne avec les autres classes Internet MFC, voir l’article [Internet Programming avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>Spécifications

**En-tête:** afxinet.h

## <a name="cinternetfileabort"></a><a name="abort"></a>CInternetFile::Abort

Ferme le fichier associé à cet objet et rend le fichier indisponible pour la lecture ou l’écriture.

```
virtual void Abort();
```

### <a name="remarks"></a>Notes

Si vous n’avez pas fermé le fichier avant de détruire l’objet, le destructeur le ferme pour vous.

Lors de `Abort` la manipulation des exceptions, diffère de [Close](#close) de deux façons importantes. Tout d’abord, la `Abort` fonction ne jette pas d’exception sur les échecs parce qu’elle ignore les échecs. Deuxièmement, `Abort` n’affirme **pas** si le dossier n’a pas été ouvert ou a été fermé précédemment.

## <a name="cinternetfilecinternetfile"></a><a name="cinternetfile"></a>CInternetFile::CInternetFile

Cette fonction de membre `CInternetFile` est appelée lorsqu’un objet est créé.

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

*hFile (en)*<br/>
Une poignée à un fichier Internet.

*pstrFileName (en)*<br/>
Un pointeur à une chaîne contenant le nom du fichier.

*pConnection*<br/>
Un pointeur sur un objet [CInternetConnection.](../../mfc/reference/cinternetconnection-class.md)

*bReadMode (en)*<br/>
Indique si le fichier est lu uniquement.

*hSession*<br/>
Une poignée à une session Internet.

*pstrServer (en)*<br/>
Un pointeur à une chaîne contenant le nom du serveur.

*dwContexte*<br/>
L’identifiant de `CInternetFile` contexte pour l’objet. Voir [WinInet Basics](../../mfc/wininet-basics.md) pour plus d’informations sur l’identifiant contextuelle.

### <a name="remarks"></a>Notes

Vous ne `CInternetFile` créez jamais un objet directement. Au lieu de cela, créer un objet de l’une de ses classes dérivées en appelant [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) ou [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Vous pouvez également `CInternetFile` créer un objet en appelant [CFtpConnection:OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

## <a name="cinternetfileclose"></a><a name="close"></a>CInternetFile::Fermer

Ferme un `CInternetFile` et libère l’une de ses ressources.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Si le fichier a été ouvert pour la rédaction, il y a un appel implicite à [Flush](#flush) pour s’assurer que toutes les données tamponnées sont écrites à l’hôte. Vous devriez `Close` appeler lorsque vous avez terminé l’utilisation d’un fichier.

## <a name="cinternetfileflush"></a><a name="flush"></a>CInternetFile::Flush

Appelez cette fonction de membre pour rincer le contenu du tampon d’écriture.

```
virtual void Flush();
```

### <a name="remarks"></a>Notes

Utilisez `Flush` pour vous assurer que toutes les données en mémoire ont effectivement été écrites à la machine cible et pour assurer que votre transaction avec la machine hôte a été complétée. `Flush`n’est `CInternetFile` efficace que sur les objets ouverts à l’écriture.

## <a name="cinternetfilegetlength"></a><a name="getlength"></a>CInternetFile::GetLength

Retourne la taille du fichier.

```
virtual ULONGLONG GetLength() const;
```

## <a name="cinternetfilem_hfile"></a><a name="m_hfile"></a>CInternetFile::m_hFile

Une poignée au fichier associé à cet objet.

```
HINTERNET m_hFile;
```

## <a name="cinternetfileoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetFile::opérateur HINTERNET

Utilisez cet opérateur pour obtenir la poignée Windows pour la session Internet en cours.

```
operator HINTERNET() const;
```

## <a name="cinternetfileread"></a><a name="read"></a>CInternetFile::Lire

Appelez cette fonction de membre pour lire dans la mémoire donnée, à partir *de lpvBuf*, le nombre spécifié d’octets, *nCount*.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Pointeur désignant une adresse mémoire où sont lues des données de fichier.

*nCompte*<br/>
Nombre d'octets à écrire.

### <a name="return-value"></a>Valeur de retour

Nombre d'octets transférés dans la mémoire tampon. La valeur de déclaration peut être inférieure *à nCount* si la fin du fichier a été atteinte.

### <a name="remarks"></a>Notes

La fonction renvoie le nombre d’octets effectivement lu - un nombre qui peut être inférieur *à nCount* si le fichier se termine. Si une erreur se produit lors de la lecture du fichier, la fonction lance un objet [CInternetException](../../mfc/reference/cinternetexception-class.md) qui décrit l’erreur. Notez que la lecture au-delà de la fin du fichier n'est pas considérée comme une erreur et aucune exception n'est levée.

Pour s’assurer que toutes les données sont `CInternetFile::Read` récupérées, une application doit continuer à appeler la méthode jusqu’à ce que la méthode renvoie zéro.

## <a name="cinternetfilereadstring"></a><a name="readstring"></a>CInternetFile::LireString

Appelez cette fonction de membre pour lire un flux de caractères jusqu’à ce qu’il trouve un caractère newline.

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>Paramètres

*pstr*<br/>
Un pointeur à une chaîne qui recevra la ligne étant lue.

*Nmax*<br/>
Le nombre maximum de caractères à lire.

*rString (en)*<br/>
Une référence à l’objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui reçoit la ligne de lecture.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le tampon contenant des données simples récupérées à partir de l’objet [CInternetFile.](../../mfc/reference/cinternetfile-class.md) Quel que soit le type de données du tampon passé à cette méthode, il n’effectue aucune manipulation sur les données (par exemple, la conversion à Unicode), de sorte que vous devez cartographier les données retournées à la structure que vous attendez, comme si le type **de vide** <strong>\*</strong> ont été retournés.

NULL si la fin du fichier a été atteinte sans lire de données; ou, si boolean, FALSE si la fin du fichier a été atteint sans lire de données.

### <a name="remarks"></a>Notes

La fonction place la ligne résultante dans la mémoire référencée par le paramètre *pstr.* Il cesse de lire des caractères quand il atteint le nombre maximum de caractères, spécifié par *nMax*. Le tampon reçoit toujours un caractère nul de fin.

Si vous `ReadString` appelez sans appeler [d’abord SetReadBufferSize](#setreadbuffersize), vous obtiendrez un tampon de 4096 octets.

## <a name="cinternetfileseek"></a><a name="seek"></a>CInternetFile::Chercher

Appelez cette fonction de membre pour repositionner le pointeur dans un fichier précédemment ouvert.

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>Paramètres

*lOffset (en anglais)*<br/>
Compensez les octets pour déplacer le pointeur de lecture/écriture dans le fichier.

*nDe*<br/>
Référence relative pour la compensation. Il doit s’agir de l’une des valeurs suivantes : 

- `CFile::begin`Déplacez les octets *lOff de* pointeur de fichier vers l’avant dès le début du fichier.

- `CFile::current`Déplacez les octets *lOff de* pointeur de fichier de la position actuelle dans le fichier.

- `CFile::end`Déplacez les octets *lOff de* pointeur de fichier de la fin du fichier. *lOff* doit être négatif pour chercher dans le fichier existant; valeurs positives chercheront au-delà de la fin du fichier.

### <a name="return-value"></a>Valeur de retour

Le nouvel byte compensé dès le début du dossier si la position demandée est légale; sinon, la valeur n’est pas définie et un objet [CInternetException](../../mfc/reference/cinternetexception-class.md) est lancé.

### <a name="remarks"></a>Notes

La `Seek` fonction permet un accès aléatoire au contenu d’un fichier en déplaçant le pointeur d’un montant spécifié, absolument ou relativement. Aucune donnée n’est réellement lue pendant la recherche.

À l’heure actuelle, un appel à cette `CHttpFile` fonction membre n’est pris en charge que pour les données associées aux objets. Il n’est pas pris en charge pour les demandes FTP ou gopher. Si vous `Seek` appelez pour l’un de ces services non pris en compte, il vous transmettra au code d’erreur Win32 ERROR_INTERNET_INVALID_OPERATION.

Lorsqu’un fichier est ouvert, le pointeur de fichier est à 0, le début du fichier.

> [!NOTE]
> L’utilisation `Seek` peut provoquer un appel implicite à [Flush](#flush).

### <a name="example"></a>Exemple

  Voir l’exemple pour la mise en œuvre de la classe de base ( [CFile::Seek](../../mfc/reference/cfile-class.md#seek)).

## <a name="cinternetfilesetreadbuffersize"></a><a name="setreadbuffersize"></a>CInternetFile::SetReadBufferSize

Appelez cette fonction de membre pour définir la `CInternetFile`taille du tampon de lecture temporaire utilisé par un objet dérivé.

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>Paramètres

*nReadSize (en)*<br/>
Taille de la mémoire tampon voulue en octets.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Les API WinInet sous-jacentes n’effectuent pas de tampon, alors choisissez une taille tampon qui permet à votre application de lire les données efficacement, quelle que soit la quantité de données à lire. Si chaque appel à [Lire](#read) implique normalement une grande quantité de données (par exemple, quatre kilooctets ou plus), vous ne devriez pas avoir besoin d’un tampon. Toutefois, si `Read` vous appelez pour obtenir de petits morceaux de données, ou si vous utilisez [ReadString](#readstring) pour lire les lignes individuelles à la fois, puis un tampon de lecture améliore les performances de l’application.

Par défaut, `CInternetFile` un objet ne fournit aucun tampon pour la lecture. Si vous appelez cette fonction de membre, vous devez être sûr que le fichier a été ouvert pour l’accès à la lecture.

Vous pouvez augmenter la taille du tampon à tout moment, mais le rétrécissement du tampon n’aura aucun effet. Si vous appelez [ReadString](#readstring) sans première appel, `SetReadBufferSize`vous obtiendrez un tampon de 4096 octets.

## <a name="cinternetfilesetwritebuffersize"></a><a name="setwritebuffersize"></a>CInternetFile::SetWriteBufferSize

Appelez cette fonction de membre pour définir la `CInternetFile`taille du tampon d’écriture temporaire utilisé par un objet dérivé.

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>Paramètres

*nWriteSize*<br/>
Taille de la mémoire tampon en octets.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Les API WinInet sous-jacentes n’effectuent pas de tampon, alors choisissez une taille tampon qui permet à votre application d’écrire des données efficacement quelle que soit la quantité de données à écrire. Si chaque appel à [écrire](#write) implique normalement une grande quantité de données (par exemple, quatre kilooctets ou plus à la fois), vous ne devriez pas avoir besoin d’un tampon. Toutefois, si vous appelez [Écrivez](#write) pour écrire de petits morceaux de données, un tampon d’écriture améliore les performances de votre application.

Par défaut, `CInternetFile` un objet ne fournit aucun tampon pour l’écriture. Si vous appelez cette fonction de membre, vous devez être sûr que le fichier a été ouvert pour l’accès à l’écriture. Vous pouvez modifier la taille du tampon d’écriture à tout moment, mais cela provoque un appel implicite à [Flush](#flush).

## <a name="cinternetfilewrite"></a><a name="write"></a>CInternetFile::Ecrire

Appelez cette fonction de membre pour écrire dans la mémoire donnée, *lpvBuf*, le nombre spécifié d’octets, *nCount*.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Un pointeur vers le premier byte à être écrit.

*nCompte*<br/>
Spécifie le nombre d’octets à écrire.

### <a name="remarks"></a>Notes

Si une erreur se produit lors de l’écriture des données, la fonction jette un objet [CInternetException](../../mfc/reference/cinternetexception-class.md) décrivant l’erreur.

## <a name="cinternetfilewritestring"></a><a name="writestring"></a>CInternetFile::WriteString

Cette fonction écrit une chaîne non résiliée au fichier associé.

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>Paramètres

*pstr*<br/>
Un pointeur à une chaîne contenant le contenu à écrire.

### <a name="remarks"></a>Notes

Si une erreur se produit lors de l’écriture des données, la fonction jette un objet [CInternetException](../../mfc/reference/cinternetexception-class.md) décrivant l’erreur.

## <a name="see-also"></a>Voir aussi

[Classe CStdioFile](../../mfc/reference/cstdiofile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)
