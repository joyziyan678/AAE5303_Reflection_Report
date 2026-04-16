# AAE5303_Reflection_Report

To be honest, I was pretty nervous when I first started this course. My programming experience was almost zero – I had never even written a line of Python before, let alone used tools like COLMAP or OpenSplat. In the first few lectures, when Dr. Hsu talked about 3D Gaussian Splatting, NeRF, and SLAM, my brain just shut down. I really thought I would never be able to finish the project.
But slowly, something changed. The teacher was passionate, and the TAs were super patient. I kept trying to follow along, and little by little, things started to make sense. I actually began to find it interesting.
# Learning Cursor from scratch
The first real challenge was writing code. Luckily, we used Cursor – an AI powered code editor. It was a lifesaver for a complete beginner like me. I didn’t have to memorize tons of commands. Instead, I could ask questions, try things out, and learn by doing. From running PowerShell scripts to understanding what make_clip_scene.ps1 actually does, to later tweaking parameters and fixing paths – every step was bumpy, but every step also gave me a small sense of achievement.
# The group project: running it over and over again

Our task was to reconstruct the AMtown02 UAV dataset using COLMAP and OpenSplat. On paper, it sounds simple: extract a subset of images, run COLMAP, then train OpenSplat. In reality, it was full of holes.
First problem: disk space. My laptop doesn’t have much storage. The COLMAP database.db file could be several gigabytes, and the OpenSplat .ply output was huge too. I constantly had to delete old workspace folders and large files just to free up space. At one point, I even had to move some datasets to an external drive.

Second problem: the program would freeze halfway, or throw a database is locked error. After digging around, I found out it was because COLMAP processes weren’t fully closed. The fix: kill all COLMAP instances, delete database.db, *.db-wal, *.db-shm and the entire sparse folder, then rerun. I must have done this at least ten times.
The most frustrating part was the poor results. The first few 3D models had bright spots, missing parts, and the coverage area was way too small. Honestly, I felt pretty down. I thought maybe I was doing something fundamentally wrong.

Then I started talking to my classmates. We compared our output images and realised that my sampling frequency was too low – taking every 10th frame wasn’t giving enough information. So I adjusted the decimation: I took more images (smaller step size, like every 5th frame) and expanded the overall frame range. I also learned from the Week 6 lecture materials that the densification and pruning steps in 3DGS are very sensitive to the initial point cloud quality. So I went back, cleaned up my COLMAP reconstruction, and reran everything.

After more than ten tries – and many late nights watching the loss numbers slowly go down – I finally got a result that made me smile. The loss dropped from 0.227 to 0.101, a reduction of more than 55%. The final zsplat.ply file had over 2.1 million Gaussians. Seeing the clear, smooth 3D scene spin around on my screen felt really, really good.
# What I truly learned
If you ask me what the biggest takeaway from this project is, it’s not the 3DGS algorithm itself – though that is pretty cool. What I really gained is this: I learned how to face bugs on my own, how to search for solutions, how to tweak parameters, how to discuss with classmates, and how to keep trying even after failing more than ten times. That kind of persistence is something no textbook can teach you.
Another thing I really appreciated was the atmosphere of this course. The teacher was always energetic, and the guest speakers were genuinely inspiring. At first I was worried I wouldn’t be able to finish the assignments, but later I realised that as long as you’re willing to spend time, ask questions, and keep experimenting, it’s never as scary as it seems. In fact, I started to enjoy the whole cycle: run into a problem → figure it out → solve it → run into another problem. It became strangely addictive.
# I love this course format
This course was very different from other courses I’ve taken. No rote memorisation. Instead, we actually built something real. We could choose our own dataset and design our own pipeline. I found this way of learning fun and effective. Sure, the process was painful at times, but looking back, every minute was worth it.
So yeah, this course and this project will probably be one of the most memorable experiences of my graduate studies. Thank you to Dr. Hsu and the whole teaching team – for your patience, your energy, and for making me believe that even a programming beginner can do something cool.

