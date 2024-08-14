import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class VirtualStudyRoomUI {
    private VirtualStudyRoom virtualStudyRoom;
    private JFrame frame;
    private JButton createSessionBtn;
    private JButton joinSessionBtn;
    private JButton leaveSessionBtn;
    private JButton shareScreenBtn;
    private JButton startVideoChatBtn;
    private JLabel totalStudyTimeLabel;

    public VirtualStudyRoomUI(VirtualStudyRoom virtualStudyRoom) {
        this.virtualStudyRoom = virtualStudyRoom;

        // Create UI components
        frame = new JFrame("Virtual Study Room");
        createSessionBtn = new JButton("Create Session");
        joinSessionBtn = new JButton("Join Session");
        leaveSessionBtn = new JButton("Leave Session");
        shareScreenBtn = new JButton("Share Screen");
        startVideoChatBtn = new JButton("Start Video Chat");
        totalStudyTimeLabel = new JLabel("Total Study Time: 0 minutes");

        // Add action listeners
        createSessionBtn.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                virtualStudyRoom.createSession();
            }
        });

        joinSessionBtn.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                virtualStudyRoom.joinSession();
            }
        });

        leaveSessionBtn.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                virtualStudyRoom.leaveSession();
            }
        });

        shareScreenBtn.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                virtualStudyRoom.shareScreen();
            }
        });

        startVideoChatBtn.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                virtualStudyRoom.startVideoChat();
            }
        });

        // Update total study time label every second
        Timer timer = new Timer(1000, new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                totalStudyTimeLabel.setText("Total Study Time: " + virtualStudyRoom.getTotalStudyTime() + " minutes");
            }
        });
        timer.start();

        // Add components to frame
        frame.add(createSessionBtn);
        frame.add(joinSessionBtn);
        frame.add(leaveSessionBtn);
        frame.add(shareScreenBtn);
        frame.add(startVideoChatBtn);
        frame.add(totalStudyTimeLabel);

        // Show frame
        frame.setVisible(true);
    }
}
