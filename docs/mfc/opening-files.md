---
title: Ouverture de fichiers
ms.date: 11/04/2016
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
ms.openlocfilehash: 6119bf922b05c30a14d8421800e3931c4a038779
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375961"
---
# <a name="opening-files"></a>Ouverture de fichiers

Dans MFC, la façon la plus courante d’ouvrir un fichier est un processus en deux étapes.

#### <a name="to-open-a-file"></a>Ouvrir un fichier

1. Créez l’objet de fichier sans spécifier un path ou des drapeaux d’autorisation.

   Vous créez généralement un objet de fichier en déclarant une variable [CFile](../mfc/reference/cfile-class.md) sur le cadre de pile.

1. Appelez la fonction membre [Open](../mfc/reference/cfile-class.md#open) pour l’objet de fichier, en fournissant un chemin et des drapeaux d’autorisation.

   La valeur `Open` de déclaration pour sera nonzero si le fichier a été ouvert avec succès ou 0 si le fichier spécifié ne pouvait pas être ouvert. La `Open` fonction membre est prototype comme suit :

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   Les drapeaux ouverts spécifient les autorisations, telles que la lecture seulement, que vous voulez pour le fichier. Les valeurs possibles du drapeau sont définies `CFile` comme des constantes`CFile::`énumérées `CFile::modeRead`au sein de la classe, de sorte qu’elles sont qualifiées avec " comme dans . Utilisez `CFile::modeCreate` le drapeau si vous voulez créer le fichier.

L’exemple suivant montre comment créer un nouveau fichier avec autorisation de lecture/écriture (remplacer tout fichier précédent par le même chemin) :

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
> Cet exemple crée et ouvre un fichier. En cas de `Open` problèmes, l’appel peut renvoyer un `CFileException` objet dans son dernier paramètre, comme indiqué ici. La macro TRACE imprime à la fois le nom du fichier et un code indiquant la raison de l’échec. Vous pouvez `AfxThrowFileException` appeler la fonction si vous avez besoin de rapports d’erreur plus détaillés.

## <a name="see-also"></a>Voir aussi

[CFile, classe](../mfc/reference/cfile-class.md)<br/>
[CFile::Ouvert](../mfc/reference/cfile-class.md#open)<br/>
[Fichiers](../mfc/files-in-mfc.md)
