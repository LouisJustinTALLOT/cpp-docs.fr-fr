---
title: CSocketFile, classe
ms.date: 11/04/2016
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
helpviewer_keywords:
- CSocketFile [MFC], CSocketFile
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
ms.openlocfilehash: 3b969f81c0c6e1868a66aeaa1c4d9339792062df
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502446"
---
# <a name="csocketfile-class"></a>CSocketFile, classe

Objet `CFile` utilisé pour envoyer et recevoir des données sur un réseau via Windows Sockets.

## <a name="syntax"></a>Syntaxe

```
class CSocketFile : public CFile
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSocketFile::CSocketFile](#csocketfile)|Construit un objet `CSocketFile`.|

## <a name="remarks"></a>Notes

Vous pouvez attacher l' `CSocketFile` objet à un `CSocket` objet à cet effet. Vous pouvez également, et généralement, attacher l’objet `CSocketFile` à un `CArchive` objet pour simplifier l’envoi et la réception de données à l’aide de la sérialisation MFC.

Pour sérialiser (envoyer) des données, vous l’insérez dans l’archive, qui `CSocketFile` appelle des fonctions membres pour écrire des `CSocket` données dans l’objet. Pour désérialiser (recevoir) des données, vous extrayez de l’archive. L’archive peut alors appeler `CSocketFile` des fonctions membres pour lire les données de l' `CSocket` objet.

> [!TIP]
>  Outre l' `CSocketFile` utilisation de comme décrit ici, vous pouvez l’utiliser en tant qu’objet de fichier autonome, comme vous pouvez `CFile`le faire avec, sa classe de base. Vous pouvez également utiliser `CSocketFile` avec toutes les fonctions de sérialisation MFC basées sur l’archivage. Étant `CSocketFile` donné que ne prend pas `CFile`en charge toutes les fonctionnalités de, certaines fonctions de sérialisation MFC par `CSocketFile`défaut ne sont pas compatibles avec. C’est particulièrement vrai pour la `CEditView` classe. Vous ne devez pas essayer de sérialiser `CEditView` les données via un `CArchive` objet attaché `CSocketFile` à un `CEditView::SerializeRaw`objet à `CEditView::Serialize` l’aide de; utilisez à la place. La `SerializeRaw` fonction s’attend à ce que l’objet fichier ait des fonctions `Seek`, telles `CSocketFile` que, qui ne possède pas.

Quand vous utilisez `CArchive` avec `CSocketFile` et `CSocket`, vous pouvez rencontrer une situation dans `CSocket::Receive` laquelle entre une boucle ( `PumpMessages(FD_READ)`par) en attente de la quantité d’octets demandée. Cela est dû au fait que Windows Sockets n’autorise qu’un seul appel de `CSocketFile` réception `CSocket` par notification FD_READ, mais autorise plusieurs appels recv par FD_READ. Si vous recevez un FD_READ lorsqu’il n’y a aucune donnée à lire, l’application se bloque. Si vous ne recevez jamais un autre FD_READ, l’application cesse de communiquer sur le Socket.

Vous pouvez résoudre ce problème comme suit. Dans la `OnReceive` méthode de votre classe Socket, appelez `CAsyncSocket::IOCtl(FIONREAD, ...)` avant d’appeler la `Serialize` méthode de votre classe de message lorsque les données attendues à lire à partir du socket dépassent la taille d’un paquet TCP (unité de transmission maximale du support réseau. , généralement au moins 1096 octets). Si la taille des données disponibles est inférieure à celle nécessaire, attendez que toutes les données soient reçues, puis démarrez l’opération de lecture.

Dans l’exemple suivant, `m_dwExpected` représente le nombre approximatif d’octets que l’utilisateur s’attend à recevoir. Il est supposé que vous le déclarez ailleurs dans votre code.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

Pour plus d’informations, consultez [Windows Sockets dans MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: Utilisation de sockets avec](../../mfc/windows-sockets-using-sockets-with-archives.md)des archives, ainsi que l' [API Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>Configuration requise

**En-tête:** AfxSock. h

##  <a name="csocketfile"></a>  CSocketFile::CSocketFile

Construit un objet `CSocketFile`.

```
explicit CSocketFile(
    CSocket* pSocket,
    BOOL bArchiveCompatible = TRUE);
```

### <a name="parameters"></a>Paramètres

*pSocket*<br/>
Socket à attacher à l' `CSocketFile` objet.

*bArchiveCompatible*<br/>
Spécifie si l’objet fichier est destiné à être `CArchive` utilisé avec un objet. Transmettez la valeur false uniquement si vous `CSocketFile` souhaitez utiliser l’objet de manière autonome, comme vous le feriez pour `CFile` un objet autonome, avec certaines limitations. Cet indicateur change la façon `CArchive` dont l’objet attaché `CSocketFile` à l’objet gère sa mémoire tampon pour la lecture.

### <a name="remarks"></a>Notes

Le destructeur de l’objet se dissocie de l’objet Socket lorsque l’objet est hors de portée ou est supprimé.

> [!NOTE]
>  Un `CSocketFile` peut également être utilisé en tant que fichier (limité) `CArchive` sans objet. Par défaut, le `CSocketFile` paramètre *bArchiveCompatible* du constructeur a la valeur true. Cela spécifie que l’objet fichier est destiné à être utilisé avec une archive. Pour utiliser l’objet fichier sans Archive, transmettez FALSe dans le paramètre *bArchiveCompatible* .

Dans son mode «compatible Archive», un `CSocketFile` objet offre de meilleures performances et réduit le risque d’un blocage. Un blocage se produit lorsque les sockets d’envoi et de réception sont attendus l’un l’autre, ou pour une ressource commune. Cette situation peut se produire si `CArchive` l’objet fonctionnait `CSocketFile` de la même manière qu’avec `CFile` un objet. Avec `CFile`, l’archive peut supposer que si elle reçoit moins d’octets que le nombre demandé, la fin du fichier a été atteinte.

Toutefois `CSocketFile`, avec, les données sont basées sur des messages; la mémoire tampon peut contenir plusieurs messages. par conséquent, la réception d’un nombre inférieur au nombre d’octets demandés n’implique pas la fin du fichier. L’application ne se bloque pas dans ce cas comme avec `CFile`, et elle peut continuer à lire les messages à partir de la mémoire tampon jusqu’à ce que la mémoire tampon soit vide. La fonction [CArchive:: IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty) est utile pour surveiller l’état de la mémoire tampon de l’archive dans ce cas.

Pour plus d’informations sur l’utilisation `CSocketFile`de, consultez les [Articles Windows Sockets: Utilisation de sockets avec](../../mfc/windows-sockets-using-sockets-with-archives.md) des [Archives et Windows Sockets: Exemple de sockets utilisant des](../../mfc/windows-sockets-example-of-sockets-using-archives.md)Archives.

## <a name="see-also"></a>Voir aussi

[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket, classe](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocket, classe](../../mfc/reference/csocket-class.md)
