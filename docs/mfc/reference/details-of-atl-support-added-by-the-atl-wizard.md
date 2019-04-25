---
title: Détails de la prise en charge ATL ajoutée par l'Assistant ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.atl.support
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
ms.openlocfilehash: 0b849ffb585ef99512cc68e1c734dc5b3a87d507
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323318"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>Détails de la prise en charge ATL ajoutée par l'Assistant ATL

Lorsque vous [ajouter la prise en charge ATL à un exécutable MFC ou une DLL existante](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), Visual C++ apporte les modifications suivantes au projet MFC existant (dans cet exemple, le projet est appelé `MFCEXE`) :

- Deux nouveaux fichiers (un fichier .idl et un fichier .rgs, utilisé pour inscrire le serveur) sont ajoutés.

- Dans les fichiers application principale en-tête et d’implémentation (Mfcexe.h et Mfcexe.cpp), une nouvelle classe (dérivée de `CAtlMFCModule`) est ajouté. En plus de la nouvelle classe, le code est ajouté à `InitInstance` pour l’inscription. Code est également ajouté à la `ExitInstance` fonction pour révoquer l’objet de classe. Dans le fichier d’en-tête, enfin, deux nouveaux fichiers d’en-tête (Initguid.h et Mfcexe_i.c) sont inclus dans le fichier d’implémentation, déclarant et initialisant les nouveaux GUID pour le `CAtlMFCModule`-classe dérivée.

- Pour inscrire le serveur correctement, une entrée pour le nouveau fichier .rgs est ajoutée au fichier de ressources du projet.

## <a name="notes-for-dll-projects"></a>Notes de publication pour les projets DLL

Lorsque vous ajoutez la prise en charge ATL à un projet DLL MFC, vous verrez des différences. Code est ajouté à la `DLLRegisterServer` et `DLLUnregisterServer` fonctions de l’inscription et désinscription de la DLL. Code est également ajouté à [DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow) et [DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject).

## <a name="see-also"></a>Voir aussi

[Prise en charge ATL dans un projet MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Ajout d’une variable membre](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Substitution d’une fonction virtuelle](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Parcours de la structure de classe](../../ide/navigating-the-class-structure-visual-cpp.md)
