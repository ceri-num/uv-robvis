# Calibration

## PriseDeVueRobot.py

Le but c'est decrire un programe Python pour capturer les images d'une mire de calibration :
1. Calcul et Enregistrement des T_gripper2base à partir des poses de prise de vue dans le dossier T_gripper2base
2. Calcul et Enregistrement des T_Base2gripper dans le dossier T_Base2gripper 
3. Enregistrement des poistions et l'orientation des poitions de prise de vue dans le dossier JointPositions
4. Enregistrement des images de mire de calibration dans le repertoire RGBImgs

## CalibrateHandEye()

CalibrateHandEye() permet de determiner la transformation Camera dans le repere de l'outil
