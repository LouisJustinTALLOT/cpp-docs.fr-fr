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
ms.openlocfilehash: 73407eba802b7640e880b821144954fa6442f177
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622162"
---
# <a name="opening-files"></a>Ouverture de fichiers

Dans MFC, la méthode la plus courante pour ouvrir un fichier est un processus en deux étapes.

#### <a name="to-open-a-file"></a>Pour ouvrir un fichier

1. Créez l’objet de fichier sans spécifier de chemin d’accès ou d’indicateurs d’autorisation.

   En général, vous créez un objet de fichier en déclarant une variable [CFile](reference/cfile-class.md) sur le frame de pile.

1. Appelez la fonction membre [Open](reference/cfile-class.md#open) pour l’objet file, en fournissant un chemin d’accès et des indicateurs d’autorisation.

   La valeur de retour pour `Open` sera différente de zéro si le fichier a été ouvert avec succès ou 0 si le fichier spécifié n’a pas pu être ouvert. La `Open` fonction membre est prototypée comme suit :

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   Les indicateurs ouverts spécifient les autorisations, telles que lecture seule, que vous souhaitez pour le fichier. Les valeurs d’indicateur possibles sont définies en tant que constantes énumérées dans la `CFile` classe, de sorte qu’elles sont qualifiées avec « `CFile::` » comme dans `CFile::modeRead` . Utilisez l' `CFile::modeCreate` indicateur si vous souhaitez créer le fichier.

L’exemple suivant montre comment créer un fichier avec une autorisation de lecture/écriture (en remplaçant tout fichier précédent avec le même chemin d’accès) :

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
> Cet exemple crée et ouvre un fichier. En cas de problème, l' `Open` appel peut retourner un `CFileException` objet dans son dernier paramètre, comme indiqué ici. La macro TRACE imprime le nom de fichier et un code indiquant la raison de l’échec. Vous pouvez appeler la `AfxThrowFileException` fonction si vous avez besoin d’un rapport d’erreurs plus détaillé.

## <a name="see-also"></a>Voir aussi

[CFile, classe](reference/cfile-class.md)<br/>
[CFile :: Open](reference/cfile-class.md#open)<br/>
[Fichiers](files-in-mfc.md)
