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
ms.openlocfilehash: 83810a05925e5c8302240b61d95c131fdd78b426
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318163"
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

Vous pouvez `CSocketFile` attacher l’objet à un `CSocket` objet à cette fin. Vous pouvez également, et le `CSocketFile` font `CArchive` habituellement, joindre l’objet à un objet pour simplifier l’envoi et la réception de données à l’aide de la sérialisation MFC.

Pour sérialiser (envoyer) des données, vous `CSocketFile` les insérez `CSocket` dans l’archive, qui appelle les fonctions des membres pour écrire des données sur l’objet. Pour déséialiser (recevoir) des données, vous extrayez de l’archive. Cela provoque l’archive d’appeler `CSocketFile` les `CSocket` fonctions des membres pour lire les données de l’objet.

> [!TIP]
> En `CSocketFile` plus d’utiliser comme décrit ici, vous pouvez l’utiliser `CFile`comme un objet de fichier autonome, tout comme vous pouvez avec , sa classe de base. Vous pouvez `CSocketFile` également utiliser avec toutes les fonctions de sérialisation MFC basées sur les archives. Parce `CSocketFile` que ne `CFile`prend pas en charge toutes les fonctionnalités de `CSocketFile`'s, certaines fonctions de sérialisation MFC par défaut ne sont pas compatibles avec . C’est particulièrement `CEditView` vrai pour la classe. Vous ne devez pas `CEditView` essayer `CArchive` de sérialiser des données à l’aide d’un `CSocketFile` objet à l’aide de l’utilisation `CEditView::SerializeRaw`; utilisation `CEditView::Serialize` à la place. La `SerializeRaw` fonction s’attend à ce que `Seek`l’objet de fichier ait des fonctions, telles que , qui `CSocketFile` n’a pas.

Lorsque vous `CArchive` `CSocketFile` utilisez `CSocket`avec et , `CSocket::Receive` vous pouvez rencontrer `PumpMessages(FD_READ)`une situation où entre une boucle (par ) en attente du montant demandé des octets. C’est parce que les prises Windows n’autorisent qu’un seul appel de recv par FD_READ notification, mais `CSocketFile` et `CSocket` permettent plusieurs appels de recv par FD_READ. Si vous obtenez un FD_READ lorsqu’il n’y a pas de données à lire, l’application est suspendue. Si vous n’obtenez jamais un autre FD_READ, l’application cesse de communiquer sur la prise.

Vous pouvez résoudre ce problème comme suit. Dans `OnReceive` la méthode de votre `CAsyncSocket::IOCtl(FIONREAD, ...)` classe de `Serialize` prise, appelez avant d’appeler la méthode de votre classe de message lorsque les données attendues à lire à partir de la prise dépasse la taille d’un paquet TCP (unité de transmission maximale du support réseau, généralement au moins 1096 octets). Si la taille des données disponibles est inférieure aux besoins, attendez que toutes les données soient reçues et seulement alors commencez l’opération de lecture.

Dans l’exemple `m_dwExpected` suivant, se trouve le nombre approximatif d’octets que l’utilisateur s’attend à recevoir. On suppose que vous le déclarez ailleurs dans votre code.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

Pour plus d’informations, voir [Windows Sockets in MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md), ainsi que Windows [Sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>Spécifications

**En-tête:** afxsock.h

## <a name="csocketfilecsocketfile"></a><a name="csocketfile"></a>CSocketFile::CSocketFile

Construit un objet `CSocketFile`.

```
explicit CSocketFile(
    CSocket* pSocket,
    BOOL bArchiveCompatible = TRUE);
```

### <a name="parameters"></a>Paramètres

*pSocket (pSocket)*<br/>
La prise à attacher `CSocketFile` à l’objet.

*bArchiveCompatible*<br/>
Précise si l’objet de fichier `CArchive` est à utiliser avec un objet. Pass FALSE seulement si vous `CSocketFile` voulez utiliser l’objet d’une manière `CFile` autonome comme vous le feriez un objet autonome, avec certaines limitations. Ce drapeau modifie `CArchive` la façon `CSocketFile` dont l’objet attaché à l’objet gère son tampon pour la lecture.

### <a name="remarks"></a>Notes

Le destructeur de l’objet se dissocie de l’objet de prise lorsque l’objet sort de portée ou est supprimé.

> [!NOTE]
> A `CSocketFile` peut également être utilisé comme un `CArchive` fichier (limité) sans objet. Par défaut, `CSocketFile` le *paramètre bArchiveCompatible* du constructeur est VRAI. Cela spécifie que l’objet de fichier est à utiliser avec une archive. Pour utiliser l’objet de fichier sans archive, passez FALSE dans le *paramètre bArchiveCompatible.*

Dans son mode « compatible `CSocketFile` d’archive », un objet offre de meilleures performances et réduit le risque d’une « impasse ». Une impasse se produit lorsque les prises d’envoi et de réception s’attendent les unes aux autres ou pour une ressource commune. Cette situation peut `CArchive` se produire `CSocketFile` si l’objet `CFile` a fonctionné avec la façon dont il le fait avec un objet. Avec `CFile`, l’archive peut supposer que si elle reçoit moins d’octets qu’elle a demandé, la fin du fichier a été atteint.

Avec, `CSocketFile`cependant, les données sont basées sur le message; le tampon peut contenir plusieurs messages, de sorte que recevoir moins que le nombre d’octets demandés n’implique pas la fin du fichier. L’application ne bloque pas dans `CFile`ce cas comme il pourrait avec, et il peut continuer à lire des messages à partir du tampon jusqu’à ce que le tampon est vide. Le [CArchive::IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty) fonction est utile pour surveiller l’état de la mémoire tampon de l’archive dans un tel cas.

Pour plus d’informations `CSocketFile`sur l’utilisation de , voir les articles [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md) and Windows [Sockets: Exemple of Sockets Using Archives](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="see-also"></a>Voir aussi

[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CAsyncSocket](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocket, classe](../../mfc/reference/csocket-class.md)
