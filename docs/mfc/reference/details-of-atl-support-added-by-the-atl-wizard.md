---
title: Détails de la prise en charge ATL ajoutée par l'Assistant ATL
ms.date: 08/20/2019
f1_keywords:
- vc.codewiz.atl.support
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
ms.openlocfilehash: aeac01ce58deb429f14058c06524dff53abde060
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924436"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>Détails de la prise en charge ATL ajoutée par l'Assistant ATL

::: moniker range=">=msvc-160"

Quand vous [Ajoutez la prise en charge ATL à un exécutable ou une DLL MFC existante](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), Visual Studio ajoute un fichier d’en-tête appelé *Framework. h* par défaut, qui contient les `#include` directives de `#define` préprocesseur et pour activer l’utilisation des ATL dans votre projet. Aucun fichier ou classe supplémentaire n’est ajouté, comme c’était le cas dans les versions précédentes de Visual Studio.

::: moniker-end

::: moniker range="<=msvc-150"

Quand vous [Ajoutez la prise en charge ATL à un fichier exécutable ou une DLL MFC existante](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), Visual Studio apporte les modifications suivantes au projet MFC existant (dans cet exemple, le projet est appelé `MFCEXE` ) :

- Deux nouveaux fichiers (un fichier. idl et un fichier. RGS, utilisés pour inscrire le serveur) sont ajoutés.

- Dans les fichiers d’en-tête et d’implémentation de l’application principale (Mfcexe. h et Mfcexe. cpp), une nouvelle classe (dérivée de `CAtlMFCModule` ) est ajoutée. En plus de la nouvelle classe, du code est ajouté à `InitInstance` pour l’inscription. Du code est également ajouté à la `ExitInstance` fonction pour révoquer l’objet de classe. Dans le fichier d’en-tête, enfin, deux nouveaux fichiers d’en-tête (Initguid. h et Mfcexe_i. c) sont inclus dans le fichier d’implémentation, en déclarant et en initialisant les nouveaux GUID pour la `CAtlMFCModule` classe dérivée de.

- Pour inscrire le serveur correctement, une entrée pour le nouveau fichier. RGS est ajoutée au fichier de ressources du projet.

::: moniker-end

## <a name="notes-for-dll-projects"></a>Notes pour les projets DLL

Lorsque vous ajoutez la prise en charge ATL à un projet DLL MFC, vous verrez des différences. Du code est ajouté aux `DLLRegisterServer` `DLLUnregisterServer` fonctions et pour l’inscription et l’annulation de l’inscription de la dll. Le code est également ajouté à [DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow) et [DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject).

## <a name="see-also"></a>Voir aussi

[Prise en charge ATL dans un projet MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Ajout d’une variable membre](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Substitution d’une fonction virtuelle](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Parcours de la structure de classe](../../ide/navigate-code-cpp.md)
