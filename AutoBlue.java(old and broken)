package org.firstinspires.ftc.teamcode;

import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;
import com.qualcomm.robotcore.eventloop.opmode.Autonomous;
import org.firstinspires.ftc.robotcore.external.Telemetry;
import com.qualcomm.robotcore.eventloop.opmode.TeleOp;
import com.qualcomm.robotcore.hardware.DcMotor;
import com.qualcomm.robotcore.hardware.DcMotorSimple;
import com.qualcomm.robotcore.hardware.Servo;

@Autonomous(name = "Auto Blue", group = "")
public class AutoBlue extends LinearOpMode
{
		public DcMotor spinner; //Thing
		public DcMotor frontLeft; //Front left
		public DcMotor backLeft; //Back left
		public DcMotor backRight; //Back right
		public DcMotor frontRight; //Front right
		public Servo grabber_servo; //hand servo
		public DcMotor arm; //Arm
		
		//These below could have been used (in theory) to do position detection
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
					//Drive(Direction.FORWARD, 1000);
					Drive(Direction.BACKWARD, 2000);
					spinner.setPower(-.8);
					sleep(30000);
					break;
				}
		}
		public float GetSin(int time) {
			return (int)((Math.sin(rotation)*20.5f*(time/1000))*10)/10f;
		}
		public float GetCos(int time) {
			return (int)((Math.cos(rotation)*20.5f*(time/1000))*10)/10f;
		}
		
		public void Drive(Direction d, int milliseconds)
		{
			Drive(d);
			sleep(milliseconds);
			Drive(Direction.STOP);
			if(d == Direction.FORWARD)
			{
				xPos+=GetCos(milliseconds);
				yPos+=GetSin(milliseconds);
			}
			else if(d == Direction.LEFT)
			{
				xPos+=GetSin(milliseconds);
				yPos+=GetCos(milliseconds);
			}
			else if(d == Direction.RIGHT)
			{
				xPos-=GetSin(milliseconds);
				yPos-=GetCos(milliseconds);
			}
			else if(d == Direction.BACKWARD)
			{
				xPos-=GetCos(milliseconds);
				yPos-=GetSin(milliseconds);
			}
			else if(d == Direction.TURNLEFT)
			{
				rotation += 1.5707963267949f * (milliseconds/1000);
			}
			else if(d == Direction.TURNRIGHT)
			{
				rotation -= 1.5707963267949f * (milliseconds/1000);
			}
		}
		public void Drive(Direction d)
		{
				if(d == Direction.BACKWARD)
				{
					backRight.setPower(-.75);
					frontLeft.setPower(-.55); //Faulty motor
					frontRight.setPower(-.75);
					backLeft.setPower(-.75);
					//yPos -= Math.sin(rotation)*.75f;
					//xPos -= Math.cos(rotation)*.75f;
					//Rotation = 0, y inc
					//Rotation = Pi/2, x inc
				}
				else if(d == Direction.LEFT)
				{
					backRight.setPower(.75);
					frontLeft.setPower(.55); //Faulty motor
					frontRight.setPower(-.75);
					backLeft.setPower(-.75);
					//xPos += Math.sin(rotation)*.75f;
					//yPos += Math.cos(rotation)*.75f;
				}
				else if(d == Direction.RIGHT)
				{
					backRight.setPower(-.75);
					frontLeft.setPower(-.55); //Faulty motor
					frontRight.setPower(.75);
					backLeft.setPower(.75);
					//xPos -= Math.sin(rotation)*.75f;
					//yPos -= Math.cos(rotation)*.75f;
				}
				else if(d == Direction.FORWARD)
				{
					backRight.setPower(.75);
					frontLeft.setPower(.55); //Faulty motor
					frontRight.setPower(.75);
					backLeft.setPower(.75);
					//yPos += Math.sin(rotation)*.75f;
					//xPos += Math.cos(rotation)*.75f;
				}
				else if(d == Direction.TURNRIGHT)
				{
					frontRight.setPower(-.35); //Faulty motor
					backLeft.setPower(.5);
					frontLeft.setPower(.5);
					backRight.setPower(-.5);
					//rotation += 3.14159265358979f * .5f;
				}
				else if(d == Direction.TURNLEFT)
				{
					frontRight.setPower(.35); //Faulty motor
					backLeft.setPower(-.5);
					frontLeft.setPower(-.5);
					backRight.setPower(.5);
					//rotation -= 3.14159265358979f * .5f;
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
