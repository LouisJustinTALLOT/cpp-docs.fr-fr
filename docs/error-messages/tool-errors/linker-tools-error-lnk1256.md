---
title: Erreur des outils Éditeur de liens LNK1256
ms.date: 11/04/2016
f1_keywords:
- LNK1256
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
ms.openlocfilehash: 47c20f24a2fe26cc96d5efcf359652a40af508ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160573"
---
# <a name="linker-tools-error-lnk1256"></a>Erreur des outils Éditeur de liens LNK1256

Échec de l'opération ALINK : raison

Une des raisons courantes de la survenue de l'erreur LNK1256 est l'existence d'un numéro de version incorrect pour un assembly. La valeur 65 535 n'est pas autorisée, quelle que soit la partie du numéro de version de l'assembly. La plage valide pour les versions d’assembly est 0 - 65534.

L'erreur LNK1256 peut aussi survenir si ALINK n'a pas trouvé le conteneur de clé nommé. Supprimer le conteneur de clé et rajoutez-le au nom fort CSP à l’aide de [Sn.exe (Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool).

L'erreur LNK1256 peut aussi être liée à une incompatibilité de version entre l'éditeur de liens et Alink.dll. Une installation endommagée de Visual Studio peut en être la cause. Utilisez **programmes et fonctionnalités** dans le panneau de configuration Windows pour réparer ou réinstaller Visual Studio.

L'exemple suivant génère l'erreur LNK1256 :

```
// LNK1256.cpp
// compile with: /clr /LD
// LNK1256 expected
[assembly:System::Reflection::AssemblyVersionAttribute("1.0.65535")];
public class CMyClass {
public:
   int value;
};
```