---
title: Ouverture de fichiers | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Open member functions [MFC]
- CFile class [MFC], variable
- opening files, in MFC
- Open calls [MFC]
- Open method, CFile class [MFC]
- examples [MFC], opening files
- opening files, handling exceptions
- exception handling [MFC], when opening files
- files [MFC], opening
- file objects [MFC]
- MFC, file operations
- opening files [MFC]
- exception handling [MFC], opening files
ms.assetid: a991b8ec-b04a-4766-b47e-7485b5dd0b01
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f74c0fdcdb8d6dfe1aced33a1c7087ecde6c89ff
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080921"
---
# <a name="opening-files"></a>Ouverture de fichiers

Dans MFC, la méthode la plus courante pour ouvrir un fichier est un processus en deux étapes.

#### <a name="to-open-a-file"></a>Pour ouvrir un fichier

1. Créez l’objet de fichier sans spécifier un chemin d’accès ou d’autorisation des indicateurs.

   Vous créez généralement un objet fichier en déclarant un [CFile](../mfc/reference/cfile-class.md) variable sur le frame de pile.

1. Appelez le [Open](../mfc/reference/cfile-class.md#open) fonction membre de l’objet de fichier, en fournissant un chemin d’accès et d’autorisation des indicateurs.

   La valeur de retour pour `Open` sera différent de zéro si le fichier a été ouverte avec succès ou 0 si le fichier spécifié n’a pas pu être ouvert. Le `Open` fonction membre se présente comme suit :

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   Les indicateurs d’ouverture spécifient les autorisations, comme en lecture seule, vous souhaitez pour le fichier. Les valeurs possibles des indicateurs sont définies en tant que constantes énumérées dans le `CFile` classe, afin qu’ils soient qualifiés avec «`CFile::`» comme dans `CFile::modeRead`. Utilisez le `CFile::modeCreate` indicateur si vous souhaitez créer le fichier.

L’exemple suivant montre comment créer un nouveau fichier avec l’autorisation de lecture/écriture (avec le même chemin, en remplaçant tout fichier précédent) :

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
>  Cet exemple crée et ouvre un fichier. S’il existe des problèmes, le `Open` appel peut retourner un `CFileException` de l’objet dans son dernier paramètre, comme indiqué ici. La macro TRACE imprime le nom de fichier et un code indiquant la raison de l’échec. Vous pouvez appeler la `AfxThrowFileException` fonctionner si vous avez besoin de plus le rapport d’erreurs.

## <a name="see-also"></a>Voir aussi

[CFile, classe](../mfc/reference/cfile-class.md)<br/>
[CFile::Open](../mfc/reference/cfile-class.md#open)<br/>
[Fichiers](../mfc/files-in-mfc.md)

