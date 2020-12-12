---
description: 'En savoir plus sur : CSocketFile, classe'
title: CSocketFile, classe
ms.date: 11/04/2016
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
helpviewer_keywords:
- CSocketFile [MFC], CSocketFile
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
ms.openlocfilehash: 4ca484545e11502a11acf5f27b00ee2df49fc9d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318648"
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
|[CSocketFile :: CSocketFile](#csocketfile)|Construit un objet `CSocketFile`.|

## <a name="remarks"></a>Notes

Vous pouvez attacher l' `CSocketFile` objet à un `CSocket` objet à cet effet. Vous pouvez également, et généralement, attacher l' `CSocketFile` objet à un `CArchive` objet pour simplifier l’envoi et la réception de données à l’aide de la sérialisation MFC.

Pour sérialiser (envoyer) des données, vous l’insérez dans l’archive, qui appelle des `CSocketFile` fonctions membres pour écrire des données dans l' `CSocket` objet. Pour désérialiser (recevoir) des données, vous extrayez de l’archive. L’archive peut alors appeler `CSocketFile` des fonctions membres pour lire les données de l' `CSocket` objet.

> [!TIP]
> Outre l’utilisation `CSocketFile` de comme décrit ici, vous pouvez l’utiliser en tant qu’objet de fichier autonome, comme vous pouvez `CFile` le faire avec, sa classe de base. Vous pouvez également utiliser `CSocketFile` avec toutes les fonctions de SÉRIALISATION MFC basées sur l’archivage. Étant donné que `CSocketFile` ne prend pas en charge toutes les `CFile` fonctionnalités de, certaines fonctions de sérialisation MFC par défaut ne sont pas compatibles avec `CSocketFile` . C’est particulièrement vrai pour la `CEditView` classe. Vous ne devez pas essayer de sérialiser les `CEditView` données via un `CArchive` objet attaché à un `CSocketFile` objet à l’aide de `CEditView::SerializeRaw` ; Utilisez à la `CEditView::Serialize` place. La `SerializeRaw` fonction s’attend à ce que l’objet fichier ait des fonctions, telles que `Seek` , qui `CSocketFile` ne possède pas.

Quand vous utilisez `CArchive` avec `CSocketFile` et `CSocket` , vous pouvez rencontrer une situation dans laquelle `CSocket::Receive` entre une boucle (par `PumpMessages(FD_READ)` ) en attente de la quantité d’octets demandée. Cela est dû au fait que Windows Sockets n’autorise qu’un seul appel de réception par FD_READ notification, mais `CSocketFile` et `CSocket` autorise plusieurs appels de réception par FD_READ. Si vous recevez une FD_READ lorsqu’il n’y a aucune donnée à lire, l’application se bloque. Si vous ne recevez jamais un autre FD_READ, l’application cesse de communiquer sur le Socket.

Vous pouvez résoudre ce problème comme suit. Dans la `OnReceive` méthode de votre classe Socket, appelez `CAsyncSocket::IOCtl(FIONREAD, ...)` avant d’appeler la `Serialize` méthode de votre classe de message lorsque les données attendues à lire à partir du socket dépassent la taille d’un paquet TCP (unité de transmission maximale du support réseau, généralement au moins 1096 octets). Si la taille des données disponibles est inférieure à celle nécessaire, attendez que toutes les données soient reçues, puis démarrez l’opération de lecture.

Dans l’exemple suivant, `m_dwExpected` représente le nombre approximatif d’octets que l’utilisateur s’attend à recevoir. Il est supposé que vous le déclarez ailleurs dans votre code.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

Pour plus d’informations, consultez [Windows Sockets dans MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md), ainsi que l' [API Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>Spécifications

**En-tête :** AfxSock. h

## <a name="csocketfilecsocketfile"></a><a name="csocketfile"></a> CSocketFile :: CSocketFile

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
Spécifie si l’objet fichier est destiné à être utilisé avec un `CArchive` objet. Transmettez la valeur FALSe uniquement si vous souhaitez utiliser l' `CSocketFile` objet de manière autonome, comme vous le feriez pour un `CFile` objet autonome, avec certaines limitations. Cet indicateur change la façon dont l' `CArchive` objet attaché à l' `CSocketFile` objet gère sa mémoire tampon pour la lecture.

### <a name="remarks"></a>Notes

Le destructeur de l’objet se dissocie de l’objet Socket lorsque l’objet est hors de portée ou est supprimé.

> [!NOTE]
> Un `CSocketFile` peut également être utilisé en tant que fichier (limité) sans `CArchive` objet. Par défaut, le `CSocketFile` paramètre *bArchiveCompatible* du constructeur a la valeur true. Cela spécifie que l’objet fichier est destiné à être utilisé avec une archive. Pour utiliser l’objet fichier sans Archive, transmettez FALSe dans le paramètre *bArchiveCompatible* .

Dans son mode « compatible Archive », un `CSocketFile` objet offre de meilleures performances et réduit le risque d’un blocage. Un blocage se produit lorsque les sockets d’envoi et de réception sont attendus l’un l’autre, ou pour une ressource commune. Cette situation peut se produire si l' `CArchive` objet fonctionnait de la `CSocketFile` même manière qu’avec un `CFile` objet. Avec `CFile` , l’archive peut supposer que si elle reçoit moins d’octets que le nombre demandé, la fin du fichier a été atteinte.

`CSocketFile`Toutefois, avec, les données sont basées sur des messages ; la mémoire tampon peut contenir plusieurs messages. par conséquent, la réception d’un nombre inférieur au nombre d’octets demandés n’implique pas la fin du fichier. L’application ne se bloque pas dans ce cas comme avec `CFile` , et elle peut continuer à lire les messages à partir de la mémoire tampon jusqu’à ce que la mémoire tampon soit vide. La fonction [CArchive :: IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty) est utile pour surveiller l’état de la mémoire tampon de l’archive dans ce cas.

Pour plus d’informations sur l’utilisation de `CSocketFile` , consultez les articles [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md) et [Windows Sockets : exemple de sockets utilisant des archives](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="see-also"></a>Voir aussi

[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket (classe)](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocket (classe)](../../mfc/reference/csocket-class.md)
