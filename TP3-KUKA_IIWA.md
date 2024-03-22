# Présentation
Kuka iiwa 14 R820 est un robot à sept (7) degré de liberté. Il est constitué des parties suivantes : 
Base, Epaule, Coude, poignet 1, Poignet 2 et Poignet 3, R redondant.
Kuka iiwa est un robot collaboratif avec une charge utile de 14 kg
  ![kuka iiwa](./Imgs/iiwa.jpg)

# Mode de fonctionnement 

![kuka iiwa](./Imgs/mode.png)

# Les types de mouvement 

Il existe plusieurs types de déplacement :
- Mouvement point à point (PTP): Le robot guide le point central de l'outil (TCP) le long du chemin le plus rapide jusqu'au point final. Le chemin le plus rapide n'est généralement pas le chemin le plus court dans l'espace et n'est pas toujours une ligne droite. Comme les mouvements des axes du robot sont simultanés et rationnels, les trajectoires courbes peuvent être exécutées plus rapidement que les trajectoires droites.
  
  ![Mouvement PTP](./Imgs/ptp.png)
  
PTP est un mouvement de positionnement rapide. La trajectoire exacte du mouvement n'est pas prévisible ou contrôlée par le programmeur mais est toujours la même si les conditions générales n'ont pas changé.

- Mouvement linéaire (LIN) : Le robot guide le TCP à la vitesse définie le long d'une trajectoire rectiligne dans l'espace jusqu'au point final.
  
  ![Mouvement linéaire](./Imgs/lin.png)

-	Mouvement circulaire (CIRC): Le robot guide le TCP à la vitesse définie le long d'une trajectoire circulaire jusqu'au point final
 ![Mouvement circulaire](./Imgs/circ.png)

# Prise en main
Creation de nouvelle application: 
Aller dans Fichier-> Nouveau-> Application SunRise: 
 ![Nouvelle Application](./Imgs/apk1.png)
 Selectionnez Application RoboticsAPI et clicker sur ``Suivant``
 Remplacer RobotApplication par le nom de votre application: RobVis_<nom_de_votre_groupe> par exemple RobVis_3
 ![Nouvelle Application](./Imgs/apk2.png)
 Clicker sur ``Terminer`` pour créer votre application 
 Dans le fichier 

```java
Package application;


import javax.inject.Inject;
import com.kuka.roboticsAPI.applicationModel.RoboticsAPIApplication;
import static com.kuka.roboticsAPI.motionModel.BasicMotions.*;
import com.kuka.roboticsAPI.deviceModel.LBR;

/**
 * Implementation of a robot application.
 * <p>
 * The application provides a {@link RoboticsAPITask#initialize()} and a 
 * {@link RoboticsAPITask#run()} method, which will be called successively in 
 * the application lifecycle. The application will terminate automatically after 
 * the {@link RoboticsAPITask#run()} method has finished or after stopping the 
 * task. The {@link RoboticsAPITask#dispose()} method will be called, even if an 
 * exception is thrown during initialization or run. 
 * <p>
 * <b>It is imperative to call <code>super.dispose()</code> when overriding the 
 * {@link RoboticsAPITask#dispose()} method.</b> 
 * 
 * @see UseRoboticsAPIContext
 * @see #initialize()
 * @see #run()
 * @see #dispose()
 */
public class test extends RoboticsAPIApplication {
	@Inject
	private LBR lBR_iiwa_14_R820_1;

	@Override
	public void initialize() {
		// initialize your application here
	}

	@Override
	public void run() {
		// your application execution starts here
		lBR_iiwa_14_R820_1.move(ptpHome());
	}
}
```

