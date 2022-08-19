package org.firstinspires.ftc.teamcode;

import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;
import com.qualcomm.robotcore.eventloop.opmode.Autonomous;
import org.firstinspires.ftc.robotcore.external.Telemetry;
import com.qualcomm.robotcore.eventloop.opmode.TeleOp;
import com.qualcomm.robotcore.hardware.DcMotor;
import com.qualcomm.robotcore.hardware.DcMotorSimple;
import com.qualcomm.robotcore.hardware.Servo;

@Autonomous(name = "Auto Red", group = "")
public class AutoRed extends LinearOpMode
{
		public DcMotor spinner; //Thing
		public DcMotor frontLeft; //Front left
		public DcMotor backLeft; //Back left
		public DcMotor backRight; //Back right
		public DcMotor frontRight; //Front right
		public Servo grabber_servo; //hand servo
		public DcMotor arm; //Arm
		public float xPos;
		public float yPos;
		public float rotation;

		@Override
		public void runOpMode()
		{
				spinner = hardwareMap.dcMotor.get("spin");
				frontLeft = hardwareMap.dcMotor.get("front_left");
				backLeft = hardwareMap.dcMotor.get("back_left");
				backRight = hardwareMap.dcMotor.get("back_right");
				frontRight = hardwareMap.dcMotor.get("front_right");
				grabber_servo = hardwareMap.servo.get("grabber");
				arm = hardwareMap.dcMotor.get("arm");
				xPos = 0;
				yPos = 0;
				rotation = 0;
				waitForStart();
				
				spinner.setDirection(DcMotorSimple.Direction.REVERSE);
				frontLeft.setDirection(DcMotorSimple.Direction.FORWARD);
				backLeft.setDirection(DcMotorSimple.Direction.REVERSE);

				while (opModeIsActive())
				{
					//Drive forward for 1000 ms = 20.5 inches
					//Turn for 1000 ms = pi/2 rad, 90 deg, 100 grad
					Drive(Direction.FORWARD, 120);
					Drive(Direction.TURNLEFT, 925);
					Drive(Direction.BACKWARD, 1950);
					Drive(Direction.LEFT, 550);
					Drive(Direction.TURNRIGHT, 200);
					Drive(Direction.STOP);
					spinner.setPower(.4);
					sleep(30000);
					break;
					//telemetry.addData("key", "text");
					//telemetry.update();
				}
		}
		public void DriveToPos(float x, float y)
		{

		}
		public void Drive(Direction d, int milliseconds)
		{
			float xTemp = xPos;
			float yTemp = yPos;
			Drive(d);
			xTemp = (xPos - xTemp)*milliseconds;
			yTemp = (yPos - yTemp)*milliseconds;
			sleep(milliseconds);
		}
		public void Drive(Direction d)
		{
				if(d == Direction.BACKWARD)
				{
					backRight.setPower(-.75);
					frontLeft.setPower(-.5); //Faulty motor
					frontRight.setPower(-.75);
					backLeft.setPower(-.75);
					yPos += Math.sin(rotation)*.75f;
					xPos += Math.cos(rotation)*.75f;
					//Rotation = 0, y inc
					//Rotation = Pi/2, x inc
				}
				else if(d == Direction.LEFT)
				{
					backRight.setPower(.75);
					frontLeft.setPower(.5); //Faulty motor
					frontRight.setPower(-.75);
					backLeft.setPower(-.75);
					xPos += Math.sin(rotation)*.75f;
					yPos += Math.cos(rotation)*.75f;
				}
				else if(d == Direction.RIGHT)
				{
					backRight.setPower(-.75);
					frontLeft.setPower(-.5); //Faulty motor
					frontRight.setPower(.75);
					backLeft.setPower(.75);
					xPos -= Math.sin(rotation)*.75f;
					yPos -= Math.cos(rotation)*.75f;
				}
				else if(d == Direction.FORWARD)
				{
					backRight.setPower(.75);
					frontLeft.setPower(.5); //Faulty motor
					frontRight.setPower(.75);
					backLeft.setPower(.75);
					yPos -= Math.sin(rotation)*.75f;
					xPos -= Math.cos(rotation)*.75f;
				}
				else if(d == Direction.TURNRIGHT)
				{
					frontRight.setPower(-.3); //Faulty motor
					backLeft.setPower(.5);
					frontLeft.setPower(.5);
					backRight.setPower(-.5);
					rotation += 3.14159265358979f * .5f;
				}
				else if(d == Direction.TURNLEFT)
				{
					frontRight.setPower(.3); //Faulty motor
					backLeft.setPower(-.5);
					frontLeft.setPower(-.5);
					backRight.setPower(.5);
					rotation -= 3.14159265358979f * .5f;
				}
				else
				{
					frontRight.setPower(0); //Faulty motor
					backLeft.setPower(0);
					frontLeft.setPower(0);
					backRight.setPower(0);
				}
		}
		public enum Direction
		{
				FORWARD,
				LEFT,
				RIGHT,
				BACKWARD,
				STOP,
				TURNLEFT,
				TURNRIGHT,
		}
}
